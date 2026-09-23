# Changelog

All notable changes to this project are documented in this file.

## [0.1.1] — 2026-09-22

### Fixed
- **致命**：`ctx.systemPrompt.section()` 的调用签名。旧版按位置参数
  `section(name, text, order)` 调用，当前 DSH（0.1.5-rc.2）只接受单个对象
  `{ name, order, text }`，导致插件激活时抛
  `TypeError: prompt section "undefined" order must be a finite number`，
  profile 启动 fail loud（`1 entry did not activate`）。现改为对象形式。
- 欢迎语宣传了不存在的 `starter_zh action=profile`（工具 enum 里没有该动作），
  模型照做会吃到 `ToolArgsError`。改为指向插件市场/插件管理的启停与卸载。
- `peerDependencies` 范围 `^0.1.0-rc.6` 已无法被 `0.1.5-rc.2` 满足
  （semver 预发布规则），导致每次安装刷 unmet peer 警告。抬到 `^0.1.5-rc.2`。
- 移除从未 import 的死依赖 `@deepseek-ai/dsh-fs`。

## [0.1.0] — 2026-08-17

### Added
- `starter_zh` 工具：`welcome` / `path` / `plugins` / `checklist` 四个动作
- systemPrompt 新手引导提示词段（可通过 `promptEnabled` 关闭）
- 与 dsh-handbook-zh 中文教程仓库联动（`handbookUrl` 可配置）
- 纯逻辑模块 `lib/starter.js`（零依赖） + 5 个单元测试
