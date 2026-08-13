# 儿童学习困难主题网站项目计划

## 一、Summary

使用 HTML + CSS + JavaScript "三件套" 构建一个面向客户展示的儿童学习困难主题纯前端网站。项目以 iOS 扁平化设计风格为核心，通过集中式设计配置文件管理整体色调、字体、间距等视觉变量，确保全站视觉一致，并便于后期主题色多次调整。

## 二、Current State Analysis

* 项目目录 `D:\TRAE\Trae_project\lingxi_UI` 当前为空，无任何既有文件或依赖。

* 需要从零搭建目录结构、设计系统与页面。

* 无现有框架限制，可直接采用轻量级原生前端方案。

## 三、Design Requirements

1. **设计风格**：iOS 扁平化设计风格（Fluent / Apple-like）。

   * 卡片式布局、大圆角、柔和阴影、清晰的信息层级。

   * 图标使用简洁线形或填充图标，避免复杂纹理和拟物元素。
2. **色彩使用**：

   * 主色调为小面积蓝色点缀，避免商务蓝。

   * 色块以低-中饱和度为主，背景使用白色/浅灰色。

   * 整体色调、品牌色、语义色、中性色全部抽离为 CSS 变量，集中在配置文件中。
3. **一致性**：所有页面共享同一套设计令牌，确保色调与设计风格统一。

## 四、Proposed Changes

### 4.1 目录结构

```
lingxi_UI/
├── index.html              # 首页入口
├── pages/                  # 子页面
│   ├── about.html
│   ├── services.html
│   ├── cases.html
│   └── contact.html
├── css/
│   ├── tokens.css          # 设计令牌 / 配置文件
│   ├── base.css            # 重置与基础样式
│   ├── components.css      # 通用组件样式
│   └── pages.css           # 页面级样式
├── js/
│   ├── main.js             # 通用交互（导航、移动端菜单）
│   └── data.js             # 静态数据配置（如服务项、案例）
└── assets/
    ├── icons/              # SVG 图标
    └── images/             # 图片资源
```

### 4.2 新增文件及内容

#### 1. `css/tokens.css` — 设计令牌配置文件

集中管理所有视觉变量，后期修改主题色时只改此文件即可。

* **颜色变量**：

  * `--color-primary`: 主蓝色（低饱和，小面积使用）。

  * `--color-primary-light`: 主色浅色调，用于背景点缀。

  * `--color-secondary`: 辅助色（如暖黄/薄荷绿，低饱和）。

  * `--color-background`: 页面背景色（白色/浅灰）。

  * `--color-surface`: 卡片、浮层面板背景色。

  * `--color-text-primary`: 主要文本色（深灰，避免纯黑）。

  * `--color-text-secondary`: 次要文本色。

  * `--color-border`: 边框、分割线颜色。

  * `--color-success` / `--color-warning` / `--color-error`: 语义色（均低饱和）。

* **字体变量**：

  * `--font-family-base`: 系统无衬线字体栈，优先苹方/PingFang SC、思源黑体、Segoe UI。

  * `--font-size-xs` \~ `--font-size-3xl`: 字号阶梯。

  * `--font-weight-regular` / `--font-weight-medium` / `--font-weight-semibold`。

* **间距与圆角**：

  * `--space-xs` \~ `--space-3xl`。

  * `--radius-sm` \~ `--radius-xl`。

* **阴影变量**：

  * `--shadow-sm` \~ `--shadow-lg`（柔和、弥散阴影）。

#### 2. `css/base.css` — 基础样式

* 引入 `tokens.css`。

* 重置：`* { box-sizing: border-box; margin: 0; padding: 0; }`。

* `body` 设置背景色、文字色、字体、行高。

* 标题 `h1-h6` 统一字重与行高。

* 链接、列表、图片基础样式。

* 响应式断点设置（Mobile First）：

  * 默认、≥768px、≥1024px。

#### 3. `css/components.css` — 通用组件

* **导航栏**：顶部固定、白色背景、底部细线、Logo + 菜单 + CTA 按钮。

* **按钮**：主按钮（蓝色填充）、次按钮（描边/幽灵按钮）、圆角大、hover 状态。

* **卡片**：白色表面、大圆角、柔和阴影、hover 轻微上浮。

* **Hero 区域**：浅灰背景、左文右图/居中大标题、蓝色小面积点缀。

* **Feature 模块**：图标 + 标题 + 描述三列/四列布局。

* **页脚**：浅灰背景、简洁链接与版权信息。

* **表单输入**：大圆角、浅灰边框、focus 蓝色描边。

#### 4. `css/pages.css` — 页面级样式

* 首页各区块：Hero、服务介绍、成功案例、数据信任、CTA。

* 关于我们、服务详情、案例详情、联系我们等页面差异化样式。

#### 5. `js/main.js`

* 移动端导航菜单切换。

* 页面滚动时导航栏阴影变化。

* 当前页面导航高亮。

* 简单的平滑滚动锚点。

#### 6. `js/data.js`

* 静态配置：服务项目数组、案例数组、统计数据。

* 便于后期替换内容，无需改动 HTML。

#### 7. `index.html` / `pages/*.html`

* 统一引用 `tokens.css`、`base.css`、`components.css`、`pages.css`。

* 语义化 HTML 结构，ARIA 标签。

* 所有视觉属性均使用 CSS 变量，避免硬编码颜色。

### 4.3 设计规范落地细节

* **蓝色仅小面积使用**：主按钮、hover 链接、关键数据、小装饰元素。

* **背景**：`#FFFFFF` 或 `#F5F7FA` 浅灰，避免冷灰商务感。

* **卡片**：`#FFFFFF` 表面 + 浅色阴影 + `16px` 以上圆角。

* **文本**：主要 `#2C3E50` / `#1F2937`，次要 `#6B7280`，避免纯黑 `#000`。

* **按钮**：圆角 `12px`，内边距充足，字重中等。

* **图标**：使用内联 SVG 或放入 `assets/icons/`，统一 `currentColor` 控制颜色。

## 五、Assumptions & Decisions

1. **技术栈**：纯 HTML + CSS + JavaScript，不引入 Vue/React 等框架，保证展示项目轻量、易部署、易修改。
2. **图标方案**：使用内联 SVG，保证颜色与主题一致，无需额外字体图标库。
3. **页面数量**：默认 5 个页面（首页、关于我们、服务内容、成功案例、联系我们），满足客户展示需求。
4. **响应式**：优先移动端体验，适配平板与桌面端。
5. **图片资源**：初期使用占位说明，实际图片由客户提供后替换。
6. **配置化**：所有颜色、字号、间距、阴影均抽离到 `css/tokens.css`，后续主题色修改只改此文件。

## 六、Verification Steps

1. **视觉一致性检查**：

   * 打开所有 HTML 页面，确认导航、按钮、卡片、文本颜色一致。

   * 检查无硬编码颜色值（除 `tokens.css` 外）。
2. **主题色可配置验证**：

   * 修改 `tokens.css` 中 `--color-primary` 的值，刷新任意页面，确认全站蓝色点缀同步变化。
3. **响应式验证**：

   * 在浏览器 DevTools 中切换 iPhone、iPad、Desktop 尺寸，确认布局正常、导航可折叠。
4. **iOS 扁平化风格验证**：

   * 确认卡片大圆角、柔和阴影、简洁排版、无拟物/渐变装饰。
5. **交互验证**：

   * 移动端菜单可正常展开/收起。

   * 滚动时导航栏有轻微阴影变化。

   * 按钮 hover/focus 状态可见。

## 七、实施顺序

1. 创建目录结构。
2. 编写 `css/tokens.css`（设计配置文件）。
3. 编写 `css/base.css` 与 `css/components.css`。
4. 实现 `index.html` 与 `js/main.js`。
5. 实现其余页面 `pages/*.html`。
6. 跨页面一致性检查与验证。

