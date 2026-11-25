# 考拉兹猜想 · 无限飞行（Collatz Conjecture Infinite Flight）

把考拉兹猜想（3n+1 问题）变成一场无限延续的数值飞行表演：从 n=2 开始逐个起飞，偶数 ÷2、奇数 ×3+1，实时绘制每条冰雹轨迹，坠回 1 后立即测试下一个整数，永不停止。

## 特性

- **冰雹飞行轨迹**：对数高度折线图，金色峰值标记，绿色"1"基线
- **停止时间全景**：每个测过的整数化为散点，逐渐铺出考拉兹步数带状图，纪录保持者金圈高亮
- **纪录诞生榜单**：最长飞行 / 最高峰值新纪录实时播报
- **BigInt 精确运算**：峰值再大也不溢出
- 暂停 / 重置 / 速度（20–2000 步/秒），后台标签页自动兜底推进

## 算法与验证

- 迭代规则：`v = v/2（偶）或 3v+1（奇）`，直到 v=1；全程 BigInt
- 已用独立 Python 参考逐项核对纪录：n=27（111 步，峰值 9232）、n=97（118 步）、n=3711（237 步）、n=1819（峰值 1276936）等，浏览器实测完全一致

## 部署

纯静态单文件 `index.html`，零外部依赖、无构建步骤。

- **Cloudflare Workers（Git 集成）**：Workers & Pages → Create → 关联本仓库，Deploy command 设为
  `npx wrangler deploy --assets . --name petter-cloudflare-collatz-conjecture --compatibility-date 2026-11-25`
- **Cloudflare Pages**：构建命令留空，输出目录 `/`
- **GitHub Pages**：Settings → Pages → main 分支根目录

## 诚实声明

计算机已验证所有 n ≤ 2⁶⁸ ≈ 2.95×10²⁰ 都回到 1，但考拉兹猜想至今**没有被证明**。本页面是数值探索与可视化，不是证明。

姊妹项目：[黎曼猜想 · 无限延续](https://github.com/petterxy/petter_cloudflare_riemann_hypothesis)
