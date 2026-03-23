# ToolHub — AI 创意工具广场 · 页面规格文档

> 文件：`toolhub.html`
> 定位：AI 创意工具聚合平台落地页，单页面静态网站
> 技术栈：HTML + Tailwind CSS（CDN）+ 原生 JS，字体 Inter

---

## 一、整体页面结构

```
[Navbar]          导航栏（sticky top）
[Hero]            英雄区（全宽，视频背景）
[Tool Showcase]   工具广场（Tab 切换 + 卡片网格）
[Footer]
  ├── [Submit Band]   邀请提交工具
  ├── [Danmaku Zone]  实时弹幕区
  └── [Bottom Bar]    版权 + 联系方式
```

---

## 二、设计系统

### 色彩变量（Tailwind extend）

| 变量名     | 色值      | 用途             |
|-----------|-----------|-----------------|
| `page`    | `#08081A` | 页面背景         |
| `card`    | `#12132A` | 卡片背景（备用）  |
| `cardtop` | `#1A1B32` | 卡片顶部图标区   |
| `border`  | `#2A2B45` | 分割线/边框      |
| `accent`  | `#5B4FE8` | 主色调（紫蓝）   |
| `purple`  | `#8B7FFF` | 次要紫色文字     |
| `muted`   | `#8B8FA8` | 辅助文字         |
| `faint`   | `#6B6F8A` | 弱化文字         |

### 字体

- 全站：`Inter`（Google Fonts），fallback `sans-serif`

### 公共 CSS 类

| 类名                  | 说明                               |
|----------------------|------------------------------------|
| `.text-gradient`     | 白→紫渐变文字（135deg）              |
| `.tool-card`         | 卡片悬停：上移 3px + 紫色发光阴影     |
| `.hero-glow`         | Hero 区底部径向紫色光晕              |
| `.glow-border`       | 旋转彩色光圈边框动画（2.5s loop）     |
| `.ios-glass-primary` | 主要 CTA 玻璃态按钮（紫色）          |
| `.ios-glass-secondary`| 次要 CTA 玻璃态按钮（白色半透明）   |
| `.ios-glass-tabbar`  | Tab 栏玻璃态背景                    |
| `.ios-glass-card`    | 工具卡片玻璃态背景                   |
| `.ios-glass-submit`  | Footer 提交按钮（与 primary 同款）   |
| `.danmaku-input`     | 弹幕输入框（玻璃态 + focus 紫色描边） |
| `.danmaku-send-btn`  | 弹幕发送按钮（紫色渐变）             |

---

## 三、各区域详细规格

---

### 1. Navbar（导航栏）

- **样式**：`sticky top-0 z-50`，`backdrop-filter: blur(12px)`，底部 1px `border`
- **高度**：72px
- **最大宽度**：`max-w-7xl`，左右 padding `px-16`
- **左侧 Logo**：
  - 图标：36×36px，`bg-accent` 圆角 10px，emoji ⚡，字号 `text-lg`
  - 品牌名：`ToolHub`，`text-xl font-extrabold`
- **中间**：flex-1 空白占位
- **右侧导航链接**（`md:` 以上显示）：
  - 首页 / 工具广场 / 关于我们，`text-[15px]`
  - 激活状态：`text-white font-semibold`，非激活：`text-muted`
- **CTA 按钮**："提交工具 +"
  - `bg-accent hover:bg-[#6D62F0]`，`rounded-full`，`h-[38px] px-5`，`text-[14px] font-semibold`

---

### 2. Hero（英雄区）

- **背景**：`<video>` 全覆盖（`autoplay muted loop playsinline`）+ 深色蒙层（`bg-[#08081A]/70`）+ `.hero-glow` 径向光晕
- **内容区**：`max-w-4xl mx-auto`，`pt-24 pb-20`，垂直居中，`gap-7`

#### 子元素（从上到下）：

1. **Tag Pill**
   - `border border-accent/60 bg-accent/10`，`rounded-full`，`h-[30px] px-4`
   - 文字：`text-[13px] font-medium text-purple`
   - 内容：🚀 AI 创意工具聚合平台

2. **主标题**（两行）
   - 第一行：`text-[60px] font-extrabold text-white`
   - 第二行：`text-[60px] font-extrabold text-gradient`

3. **副标题**
   - `text-[17px] text-muted`，`max-w-2xl leading-relaxed`

4. **CTA 按钮组**（`flex gap-4`）
   - 主按钮"浏览工具广场"：`.ios-glass-primary`，`h-[52px] px-8 rounded-full`，`text-[16px] font-semibold`
   - 次按钮"提交我的工具"：`.ios-glass-secondary`，同尺寸，`text-[#C8C4E8] font-medium`

---

### 3. Tool Showcase（工具广场）

- **容器**：`max-w-7xl mx-auto px-16 py-16`

#### 3.1 区域标题

- 标题：`text-[32px] font-extrabold text-white`
- 副标：`text-[14px] text-faint`

#### 3.2 Tab 栏

- **容器**：`.ios-glass-tabbar border rounded-[14px] p-1`，`flex gap-1 overflow-x-auto`
- **Tab 按钮**（共 6 个）：

  | Tab Key  | 标签          |
  |---------|--------------|
  | office  | 💼 办公工具   |
  | data    | 📊 数据相关   |
  | fun     | 🎮 休闲娱乐   |
  | art     | 🎨 艺术设计   |
  | tools   | 🔧 便利小工具  |
  | other   | 📦 其他       |

- **未激活**：`text-faint font-medium`，hover `hover:text-white hover:bg-white/5`
- **激活**：`bg-accent text-white font-semibold` + `.glow-border` 旋转光圈
- **按钮尺寸**：`h-11 px-5 rounded-[10px] text-[14px] shrink-0`

#### 3.3 工具卡片

- **布局**：响应式网格
  - 移动端：1 列
  - `md`（768px+）：2 列
  - `lg`（1024px+）：3 列
  - 间距：`gap-6`

- **卡片结构**：`.tool-card .ios-glass-card border rounded-2xl overflow-hidden cursor-pointer`
  ```
  ┌─────────────────────────────┐
  │    图标区（emoji，h-24）     │  .bg-cardtop（高 96px，居中 text-5xl）
  ├─────────────────────────────┤
  │    分类徽章（小胶囊）         │  badge，rounded-full，text-[11px]
  │    工具名称                  │  text-[16px] font-bold text-white
  │    工具描述                  │  text-[13px] text-muted（2行）
  ├─────────────────────────────┤  border-t border-border，mt-1 pt-2
  │  👤 开发者名    ⭐ 评分      │  text-[12px]，评分 text-amber-400
  └─────────────────────────────┘
  ```

- **分类徽章配色**：

  | 分类    | 背景色               | 边框色           | 文字色           |
  |--------|---------------------|-----------------|-----------------|
  | 办公工具 | `bg-accent/20`     | `border-accent` | `text-purple`   |
  | 数据相关 | `bg-emerald-500/20` | `border-emerald-500` | `text-emerald-400` |
  | 休闲娱乐 | `bg-amber-500/20`  | `border-amber-500`  | `text-amber-400` |
  | 艺术设计 | `bg-pink-500/20`   | `border-pink-500`   | `text-pink-400`  |
  | 便利工具 | `bg-violet-500/20` | `border-violet-500` | `text-violet-400` |
  | 其他    | `bg-slate-500/20`  | `border-slate-400`  | `text-slate-300` |

---

### 4. Footer

#### 4.1 提交工具 Band（#submit）

- **背景**：`bg-[#0E0E24]`，顶部 `border-t border-border`
- **内边距**：`py-12 px-16`
- **布局**：`flex flex-col md:flex-row items-center gap-8`
- **左侧文字**：
  - 标题：`text-[26px] font-extrabold text-white`
  - 说明：`text-[15px] text-muted`
- **右侧按钮**"立即提交工具 →"：
  - `.ios-glass-submit`，`h-12 px-7 rounded-full`，`text-[15px] font-bold text-white`
  - `href="mailto:contact@toolhub.ai"`

#### 4.2 弹幕区（Danmaku Zone）

- **背景**：`bg-[#0B0B18]`，顶部 `border-t`
- **标题行**：💬 实时弹幕（`text-[13px] font-semibold text-purple`）
- **输入框**：`.danmaku-input`，`h-8 w-44 px-3 rounded-full text-[13px]`，最大 30 字
- **发送按钮**：`.danmaku-send-btn`，`h-8 px-4 rounded-full text-[13px] font-semibold`
- **弹幕滚动**：两行，`.danmaku-inner`（`marquee` 动画）
  - 第 1 行：`text-muted`，40s 正向
  - 第 2 行：`text-faint`，50s 反向

#### 4.3 底部版权栏

- **背景**：`bg-[#030308]`，高度 `h-14`
- **左侧**：`© 2025 ToolHub · All rights reserved`，`text-[13px] text-[#3A3D5A]`
- **右侧链接**：📧 邮箱 / 🐙 GitHub / 💬 Discord，hover `text-muted`

---

## 四、交互行为

### Tab 切换（`switchTab(key)`）

1. 隐藏所有 `.tab-panel`（移除 `active` 类）
2. 显示目标 panel（添加 `active` 类）
3. 重置所有 `.tab-btn` 到未激活样式
4. 激活目标 tab 按钮：添加 `active-tab glow-border bg-accent text-white font-semibold`

### 弹幕发送（`sendDanmaku()`）

1. 读取输入内容，随机选一个 emoji 前缀拼接
2. 向两行 `.danmaku-inner` 各追加 2 个 `<span>`（高亮色 `#c4b5fd`，`font-weight: 600`）
3. 按钮显示"✅ 已发送"并 disabled 1.5s 后恢复

---

## 五、动画规格

| 动画名        | 属性             | 规格                          |
|-------------|-----------------|-------------------------------|
| `glow-spin`  | `--glow-angle`  | 0deg → 360deg，2.5s linear infinite |
| `marquee`    | `translateX`    | 0 → -50%，40s/50s linear infinite |
| 卡片 hover   | `transform`     | `translateY(-3px)`，`transition: 0.2s` |

---

## 六、响应式断点

| 断点   | 宽度    | Tab 网格列数 |
|-------|---------|------------|
| 默认   | < 768px | 1 列       |
| `md`  | 768px+  | 2 列       |
| `lg`  | 1024px+ | 3 列       |

---

## 七、当前数据（示例工具）

每个 Tab 各 3 张卡片，共 18 张：

| 分类    | 工具名              | 开发者  | 评分  |
|--------|--------------------|----|-----|
| 办公工具 | AI 会议纪要助手      | A  | 4.8 |
| 办公工具 | 智能邮件起草器        | B  | 4.7 |
| 办公工具 | PPT 大纲生成器       | C  | 4.9 |
| 数据相关 | 数据可视化生成器      | D  | 4.6 |
| 数据相关 | SQL 查询优化器       | E  | 4.5 |
| 数据相关 | 数据清洗助手         | F  | 4.7 |
| 休闲娱乐 | AI 故事生成器        | G  | 4.9 |
| 休闲娱乐 | 角色扮演剧本          | H  | 4.8 |
| 休闲娱乐 | 歌词创作助手          | I  | 4.6 |
| 艺术设计 | AI 配色方案助手      | J  | 4.7 |
| 艺术设计 | 字体搭配推荐          | K  | 4.5 |
| 艺术设计 | Logo 创意描述器      | L  | 4.8 |
| 便利工具 | 智能文本压缩工具      | M  | 4.5 |
| 便利工具 | 翻译润色助手          | N  | 4.8 |
| 便利工具 | 时区会议助手          | O  | 4.6 |
| 其他    | AI 名字生成器         | P  | 4.4 |
| 其他    | 代码注释生成器         | Q  | 4.7 |
| 其他    | 学习计划制定器         | R  | 4.6 |
