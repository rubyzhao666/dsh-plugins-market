# ruby zhao's DSH plugins（format-1 市场索引）

三个为 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 开发的插件，可以通过本仓库的 format-1 索引一键发现和安装。

**索引地址**：

```
https://raw.githubusercontent.com/rubyzhao666/dsh-plugins-market/main/index.json
```

在 DSH 里打开 **Plugins → Discover → 添加索引源**（或 Settings 里的插件市场设置），填入上面的 URL 即可看到这三个插件并安装。


## 最新版本


- **v0.5.0（2026-11-06）**：三个插件左侧栏页全部重做为工作台式界面（TubeInsight 视频工作台 / PRD Creator 项目工作台 / Paper2HTML 论文库），主题自适应、搜索筛选、动作按钮通过新会话执行
- **v0.4.3 / v0.4.1（2026-11-06）**：左侧栏名称改为产品名（TubeInsight / Paper2HTML / PRD Creator）
- **v0.4.2 / v0.4.0（2026-11-06）**：三个插件统一换新图标；PRD Creator 新增左侧栏「PRD 项目」入口（三个插件现在都带左侧栏）
- **v0.4.1 / v0.3.3（2026-11-06）**：三个插件描述统一加品牌前缀「Ruby 出品 · DSH 插件：…」（无功能变更）
- **v0.4.0（2026-11-06）**
  - `dsh-tube-insight`：新增左侧栏「视频库」入口 + Host 只读视频库/转录页（搜索、时间戳、XSS 转义）
  - `dsh-paper2html`：新增左侧栏「论文阅读」入口（iframe 复用 /paper2html/ 论文库页面）
- **v0.3.2（2026-11-06）**
  - `dsh-prd-generator`：插件显示名改为 **PRD Creator**（Plugins 卡片 / 市场 / README / 生成的 PRD 页脚）；内部包名与 skill id 不变
- **v0.3.1（2026-11-06）**
  - 三个插件：随包 skill 与 README 改为「用户原话触发」，明确不用记工具名（无代码逻辑变更）
- **v0.3.0（2026-11-06）**
  - `dsh-tube-insight`：新增 `tube_synthesis` 主题综述证据底稿（多词检索合并、按视频分组、可一键落盘）
  - `dsh-prd-generator`：新增 `prd_handoff` 执行前门禁 + 六章 handoff.md（交给 Ralph / coding agent 前的人审门）
  - `dsh-paper2html`：批注同步进 DSH Web 预览（Host 侧存储 + 同源 API），新增 `paper2html_annotations` 让 agent 读取用户批注
- **v0.2.0（2026-11-06）**
  - `dsh-tube-insight`：新增 `tube_search` 跨视频检索 + skill 回忆/综述工作流
  - `dsh-prd-generator`：新增假设与待确认问题账本（三产物同步 + prd_check 硬规则）
  - `dsh-paper2html`：新增页面内批注/高亮 + 带批注导出分享
- v0.1.0（2026-11-06）：三个插件的首个发布版本

## 插件

| 插件 | 说明 | 仓库 |
|---|---|---|
| `dsh-tube-insight` | YouTube 链接 → 带 `[MM:SS]` 引用的洞察 / 产品情报 / PRD / 多视频对比 / 知识卡片；不需要 Chrome 扩展，不需要 Supadata key | https://github.com/rubyzhao666/dsh-tube-insight |
| `dsh-prd-generator` | 需求澄清 → PRD → ralph 兼容 `prd.json` → 验收清单，5 个文件一次生成并严格校验 | https://github.com/rubyzhao666/dsh-prd-generator |
| `dsh-paper2html` | arXiv / PDF → 单文件交互式 HTML 阅读页（三主题、可分享），无 API key 可跑 | https://github.com/rubyzhao666/dsh-paper2html |

## 手动安装

```bash
# 方式 1：在 DSH 对话里让 agent 安装（推荐）
#   "从这个仓库安装 ..." 或直接给 plugin_manager 的 install_bundle 目标：
#   git+https://github.com/rubyzhao666/dsh-tube-insight.git#<commit>
# 方式 2：拿到仓库后，用本地目录安装
plugin_manager { action: "install_bundle", target: "/path/to/dsh-tube-insight" }
```

## 索引格式

本文件是 `@deepseek-ai/dsh-plugin-market-index` 的 **format 1** 索引，每个版本用 commit 锁定 git 源：

```json
{
  "format": 1,
  "title": { "en": "...", "zh": "..." },
  "plugins": [ { "name": "dsh-tube-insight", "versions": [ { "version": "0.1.0", "source": { "type": "git", "url": "https://github.com/rubyzhao666/dsh-tube-insight", "commit": "<40-hex>" } } ] } ]
}
```

版本更新流程：插件仓库打 tag 发版 → 更新本仓库 `index.json` 里的 `version` / `publishTimestamp` / `commit`。

## 许可

MIT。三个插件均基于 ruby zhao 的上游项目（MIT）改造，版权与来源见各自仓库的 `LICENSE` 与 README。
