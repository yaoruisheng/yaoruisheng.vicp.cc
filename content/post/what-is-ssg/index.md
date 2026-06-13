+++
title = "什么是 SSG（静态网站生成器）"
description = "从 Hugo、Hexo 到 Cloudflare Pages，一文看懂 SSG（Static Site Generator）的工作原理、优势与应用场景。"

slug = "what-is-ssg"

date = 2026-06-13T00:00:00+08:00
lastmod = 2026-06-13T00:00:00+08:00

draft = false

categories = [
"互联网世界"
]

tags = [
"SSG",
"静态网站生成器",
"Hugo",
"Hexo",
"Jekyll",
"Astro",
"Next.js",
"Cloudflare Pages",
"EdgeOne Pages",
"GitHub Pages"
]

keywords = [
"SSG",
"Static Site Generator",
"静态网站生成器",
"Hugo教程",
"Hexo教程"
]
toc = true
+++

# 什么是 SSG（静态网站生成器）

刚接触 Hugo、Hexo 或 Cloudflare Pages 时，经常会看到一个缩写：**SSG**。

SSG 的全称是：

> **Static Site Generator（静态网站生成器）**

简单来说，SSG 会把你编写的 Markdown 文章、主题模板和配置文件提前生成 HTML 页面，然后直接部署到服务器或 CDN 上供用户访问。

---

## SSG 的工作原理

SSG 的核心流程如下：

```text
Markdown文章
      +
主题模板
      +
配置文件
      ↓
生成
      ↓
HTML + CSS + JS
```

例如：

你编写一篇 Markdown 文章：

```markdown
# Hello World

这是我的第一篇文章。
```

Hugo 或 Hexo 在构建时会将其转换为：

```html
<h1>Hello World</h1>
<p>这是我的第一篇文章。</p>
```

最终生成的网站目录通常类似：

```text
public/
├── index.html
├── about/index.html
├── posts/hello-world/index.html
├── css/
├── js/
└── images/
```

这些文件可以直接上传到：

* Cloudflare Pages
* EdgeOne Pages
* GitHub Pages
* Nginx
* Apache
* 对象存储 + CDN

即可对外提供访问。

---

## 为什么叫“静态网站”？

这里的“静态”并不是指页面内容永远不变，而是指：

> 用户访问时，服务器直接返回已经生成好的 HTML 文件。

不需要实时执行程序。

---

## 动态网站是如何工作的？

传统网站通常采用：

```text
浏览器
  ↓
Web服务器
  ↓
PHP
  ↓
MySQL
  ↓
生成HTML
  ↓
返回浏览器
```

例如：

* WordPress
* Discuz
* DedeCMS
* 帝国CMS

用户每访问一次页面：

1. PHP 执行程序
2. 查询数据库
3. 组装页面
4. 返回 HTML

因此服务器需要持续运行。

---

## SSG 网站是如何工作的？

SSG 网站的流程则完全不同：

```text
写文章
 ↓
构建网站
 ↓
生成HTML
 ↓
上传服务器
```

用户访问时：

```text
浏览器
 ↓
CDN
 ↓
HTML
```

整个过程中：

* 不需要 PHP
* 不需要 MySQL
* 不需要数据库查询
* 不需要运行后端程序

因此访问速度通常非常快。

---

## 为什么越来越多人使用 SSG？

### 1. 访问速度快

页面已经提前生成。

用户访问时：

```text
CDN → HTML
```

无需等待数据库查询和程序执行。

---

### 2. 部署简单

只需要部署静态文件。

例如：

```bash
hugo
```

生成：

```text
public/
```

然后上传即可。

---

### 3. 安全性高

没有：

* 后台管理系统
* PHP 程序
* 数据库

攻击面大幅减少。

例如常见的：

* SQL 注入
* PHP 漏洞
* 后台爆破

基本不存在。

---

### 4. 成本低

很多平台免费即可运行：

* GitHub Pages
* Cloudflare Pages
* EdgeOne Pages

个人博客几乎零成本。

---

## 常见的 SSG 工具

### Hugo

目前最流行的静态网站生成器之一。

特点：

* Go 语言开发
* 编译速度极快
* 单文件部署
* 适合博客和文档站

很多几千篇文章的网站也能在数秒内完成构建。

---

### Hexo

Node.js 生态中的经典博客框架。

特点：

* 中文用户多
* 主题丰富
* 插件众多
* 上手简单

曾经是国内博客圈最流行的方案之一。

---

### Jekyll

GitHub Pages 官方支持。

特点：

* Ruby 生态
* 历史悠久
* 文档丰富

很多早期技术博客都基于 Jekyll。

---

### Astro

近年来非常热门。

特点：

* 性能优秀
* 现代前端架构
* 适合博客、文档和企业官网

---

### Next.js

严格来说不仅仅是 SSG。

支持：

* SSG
* SSR
* ISR
* 客户端渲染

适合大型网站和 Web 应用。

---

## SSG 与 SSR 的区别

| 项目       | SSG                    | SSR                   |
| -------- | ---------------------- | --------------------- |
| 全称       | Static Site Generation | Server Side Rendering |
| 页面生成时间   | 构建时                    | 用户访问时                 |
| 是否需要运行程序 | 否                      | 是                     |
| 数据库      | 通常不需要                  | 通常需要                  |
| 部署难度     | 简单                     | 较复杂                   |
| 访问速度     | 极快                     | 较快                    |
| 运维成本     | 很低                     | 较高                    |
| 适用场景     | 博客、文档站                 | 电商、社区、后台系统            |

---

## 以 Hugo 博客为例

假设你写了一篇文章：

```markdown
# 我的第一篇文章

你好，世界！
```

执行：

```bash
hugo
```

生成：

```html
<h1>我的第一篇文章</h1>
<p>你好，世界！</p>
```

随后通过 GitHub Actions 自动构建：

```text
Markdown
    ↓
Hugo
    ↓
HTML
    ↓
GitHub Actions
    ↓
Cloudflare Pages
```

或者：

```text
Markdown
    ↓
Hugo
    ↓
HTML
    ↓
GitHub Actions
    ↓
EdgeOne Pages
```

用户访问时：

```text
浏览器
    ↓
CDN
    ↓
HTML
```

整个过程中无需数据库和后端程序。

---

## SSG 的缺点

虽然 SSG 很优秀，但也并非万能。

例如：

### 不适合实时交互系统

如：

* 论坛
* 在线商城
* 社交网站
* 即时聊天系统

这些场景需要动态生成内容。

---

### 大量动态数据处理较麻烦

例如：

* 用户中心
* 在线订单
* 实时库存

通常需要额外引入 API 服务。

---

## 总结

SSG（Static Site Generator）是一种预先生成 HTML 页面的网站构建方式。

其核心思想是：

> 提前生成页面，而不是访问时生成页面。

对于以下场景：

* 个人博客
* 技术文档
* 产品官网
* 项目主页
* 政府公开信息网站

SSG 往往是最简单、最快速、最省钱的解决方案。

如果你正在使用 Hugo，那么你已经在使用目前最优秀的 SSG 之一了。
