# 星愿食堂 · 抽卡点外卖小程序设计

通过抽卡帮助用户决定“今天吃什么”。本仓库收录现有可交互原型、全部已找到的设计稿、完整交互流程说明和生成脚本。

当前交付为 React + Vite 的 H5 可交互原型，可在浏览器演示小程序的核心体验；尚未接入外卖下单、支付、配送或微信小程序原生工程。

## 快速运行

需要 Node.js 18+。

```bash
npm install
npm run dev
```

打开终端显示的本地地址。构建：`npm run build`；预览构建：`npm run preview`。

## 设计稿与交互文档

- [完整交互流程 PDF（10 页）](output/pdf/star-kitchen-interaction-flow.pdf)
- [交互稿目录与逐页预览](docs/interaction/README.md)
- 首页：[PNG](exports/star-kitchen-home-preview.png) · [可编辑 SVG](exports/star-kitchen-home-preview.svg)
- 抽卡结果：[PNG](exports/star-kitchen-result-preview.png) · [可编辑 SVG](exports/star-kitchen-result-preview.svg)
- [交互流程 PDF 生成脚本](scripts/create_star_kitchen_flow_pdf.py)

### 首页

![首页设计稿](exports/star-kitchen-home-preview.png)

### 抽卡结果

![抽卡结果设计稿](exports/star-kitchen-result-preview.png)

## 原型已包含的交互

- 口味心情筛选：全部、暖呼呼、元气饭、清爽爽、快乐餐。
- 点击抽取、手机摇动触发与权限申请、约 1.45 秒抽卡动画。
- 结果揭晓、“再想想”重抽、“就吃这个”确认。
- 每天 3 次机会、当天优先避免重复、无候选或次数用尽时禁用抽取。
- 今日召唤记录与清空当天记录。
- 家长设置弹层：新增、启用、停用、删除食物，设置图标与口味分类。
- 食物库和抽取记录使用浏览器 localStorage 保存。

手机摇动依赖设备与浏览器支持，通常需要 HTTPS 和用户授予权限；桌面浏览器可直接点击抽取。

## 文件结构

```text
src/                          原型源码与样式
exports/                      首页、结果页 PNG 和 SVG
output/pdf/                   完整交互流程 PDF
scripts/                      PDF 生成脚本
  create_star_kitchen_flow_pdf.py
docs/interaction/             全部交互页预览、版本说明和文件索引
```

PDF 生成脚本依赖 Python 的 `reportlab`，并沿用原稿使用的 macOS Arial Unicode 字体路径；其他系统需先调整 `FONT_PATH`。已导出的 PDF 可以直接阅读，无需重新生成。

交互文档记录设计规则与后续小程序方向；实际已实现的行为以 `src/App.jsx` 为准。
