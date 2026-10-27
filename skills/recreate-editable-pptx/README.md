# recreate-editable-pptx

将图片、扫描版或图片型 PPT/PPTX、PDF 幻灯片复刻为对象级可编辑的 PowerPoint `.pptx`。技能会保留可识别的文字、版式、形状、连接线和必要的演讲者备注；复杂插画在无法可靠重绘时可以保留为局部图片素材，以维持视觉一致性。

## 适用场景

- 上传单页或多页幻灯片截图，要求生成可编辑 PPTX。
- 将扫描版、图片型 PPT/PPTX 或 PDF 转为可编辑对象。
- 需要在重建后进行结构验证、渲染检查和最终 PPTX 组装。

不用于从零创作普通演示文稿；这类请求应使用演示文稿创作工作流。

## 使用方式

在 Codex 中上传图片或输入文件，然后直接说：

```text
使用 recreate-editable-pptx，把这张图片复刻成可编辑 PPTX。
```

技能入口是 `SKILL.md`。其中的 `references/`、`prompts/`、`scripts/` 和 `cli/` 文件共同组成运行时，不要只复制入口文件。

## 目录说明

| 路径 | 用途 |
| --- | --- |
| `SKILL.md` | 技能入口、适用边界和工作流 |
| `agents/openai.yaml` | Codex 界面显示名称与默认提示词 |
| `references/` | CLI、清单格式和页面决策规则 |
| `prompts/` | 页面重建 worker 的执行模板 |
| `scripts/` | 生成页面 worker 提示词的辅助脚本 |
| `cli/` | `editppt` 运行时与 PPTX 验证工具 |

## 设计原则

1. 先准备输入和页面运行目录，再按页面记录清单构建 PPTX。
2. 语义文字、形状、连接线和重复结构优先使用 PowerPoint 原生对象。
3. 最终交付前执行结构验证和渲染检查，修复实际的文字或布局偏差。
4. 不把整页源图作为“可编辑重建”的替代物。

## 运行时依赖

CLI 依赖见 `cli/pyproject.toml` 和 `cli/uv.lock`。首次运行前按 `references/cli-helper.md` 中的 Pre-Run Check 安装或验证 `editppt`。

## 许可证与来源

本目录是本地已安装的 `image-to-editable-ppt` skill 的可发布副本，入口名称调整为 `recreate-editable-pptx`，以匹配用户调用名。请在仓库中按项目既有许可证和贡献规范补充许可证信息。
