# Deep Code Dive: AI 时代源码深度学习与架构考古 Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Awesome-AI-Skills](https://img.shields.io/badge/Awesome-AI--Skills-green.svg)](https://github.com)

> **拒绝空洞的设计模式套话与大模型的“事后合理化”。将源码认知推向决策层、历史妥协与失效边界。**

---

## 为什么需要这个 Skill？

大语言模型（LLM）让分析调用链、生成时序图和拆解模块变得极其便宜。然而，很多工程师在用 AI 读完代码后，仍然不敢动手重构，在线上故障发生时依然缺乏判断力。

**核心症结在于：AI 具有天然的“合理化幻觉”**。
当你问 AI “这里为什么这么设计”，它会把一个充满历史妥协、紧急 Bug 补丁或性能让步的现实工程，包装成完美契合 SOLID 原则的象牙塔。

本 Skill（`deep-code-dive`）是一套嵌入 AI 助手的元规则约束，强制模型将知识拆解为三层，并执行严格的证据分级与不变量分析：

```
 ▲
 ├── 【边界层】 When it breaks (失效条件 / 成本不对称 / 不变量)  <-- [极贵：AI不会主动给，核心护城河]
 │
 ├── 【决策层】 Why / Why not (历史约束 / 放弃的方案 / 妥协代价)   <-- [陷阱：AI最爱编故事，必须代码考古]
 │
 └── 【结构层】 What / How (模块分工 / 调用链 / 数据流)           <-- [极廉价：交由静态图谱与LLM加速]
```

---

## 核心机制与约束

1. **结构不等于因果**：代码事实（How/What）只用极简路径与 `file:line` 标注，不产生长篇废话。
2. **强制三栏分级（Observed / Inferred / Unknown）**：
   - `[Observed]`：源码字面逻辑、作者保留的 hack 注释、Git 提交记录等客观事实。
   - `[Inferred]`：逻辑推断，严禁伪装成既成事实。
   - `[Unknown]`：未确证的历史盲区。
3. **寻找工程妥协**：重点挖掘代码中的 `hack`、`gross`、`poor heuristic`、`workaround` 与 Issue 跟踪编号。
4. **不变量与成本分析**：剖析系统最昂贵的资源消耗（如跨网络 I/O、GC 抖动、主线程卡顿、线程饥饿），阐明系统为了防止哪种灾难设立了不可侵犯的规则。
5. **三重验收交付**：提供脱离 AI 即可进行的 Explain / Predict / Intervene 验收测试题。

---

## 全平台安装与使用指南

### 1. Google Antigravity
本 Skill 完全遵循 Antigravity 原生 Skill 规范：
- 将本项目文件夹拷贝到：
  - 全局技能：`~/.gemini/config/skills/deep-code-dive/`
  - 或项目技能：`.gemini/skills/deep-code-dive/`
- 在对话中直接激活，或提出：“*请用 deep-code-dive 帮我分析这个框架的缓存与生命周期调度*”。

### 2. ChatGPT (Custom GPT / Projects)
- 打开 **ChatGPT** -> **Explore GPTs** -> **Create a GPT**（或进入 Project 的 Instructions）。
- **Name**: `Code Archaeologist (源码考古家)`
- **Instructions**: 直接复制本项目中的 `prompt.txt` 内容粘贴进去。
- 开启 Code Interpreter，方便上传本地代码或补丁进行分析。

### 3. Workbuddy / Claude Code
- 支持作为自定义指令或 Slash Command（如 `/dive`）。
- 将 `prompt.txt` 配置到项目根目录的 `.claude/commands/dive.md` 或全局系统提示词中。

### 4. Cursor / Windsurf
- 复制 `prompt.txt` 内容追加到 `.cursorrules` 或 `.windsurfrules` 中，即可对当前工程的代码解释生效。

---

## 目录结构

```
deep-code-dive/
├── SKILL.md                          # Antigravity / Agent 标准技能定义文件
├── README.md                         # 项目说明与方法论指引
├── prompt.txt                        # 通用大模型系统提示词（ChatGPT / Claude / Cursor）
└── templates/
    └── reading-note-template.md      # 源码学习记录卡与决策卡模板
```

---

## 许可证

[MIT License](LICENSE)
