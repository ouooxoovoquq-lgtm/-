# 智能日报助手（静态版）

纯前端单页工具：上传工作截图 / 短视频素材，调用大模型按规范生成结构化工作日报。

- 技术栈：原生 HTML + CSS + JavaScript（单文件 `index.html`），Markdown 渲染用本地 `marked.min.js`
- 无后端、无 npm 依赖、无需构建：直接静态托管即可运行
- 模型接口由浏览器直连（千帆 / 火山方舟豆包 / OneAPI），密钥保存在浏览器 `localStorage`，不上传任何服务器

## 本地运行

```bash
cd daily-report-assistant
python3 -m http.server 8080 --bind 127.0.0.1
# 打开 http://127.0.0.1:8080/
```

## 配置模型密钥

页面左侧「模式设置」中填写对应平台的 API Key（保存到浏览器本地）。仓库内不包含任何密钥。

| 平台 | 接口地址 | 默认模型 |
| --- | --- | --- |
| 百度千帆 | `https://qianfan.baidubce.com/v2/chat/completions` | `ernie-4.5-turbo-vl` |
| 火山方舟豆包 | `https://ark.cn-beijing.volces.com/api/v3/chat/completions` | `ep-m-20260714183735-5k2hx` |
| Kimi（内部 OneAPI） | `https://oneapi-comate.baidu-int.com/v1/chat/completions` | `Kimi-K2.6` |

## 部署到 GitHub Pages

仓库推送后，在仓库 **Settings → Pages → Build and deployment** 中选择：
`Source: Deploy from a branch` → `Branch: main` → `/(root)` → Save。

约 1 分钟后访问 `https://<用户名>.github.io/<仓库名>/`。之后每次 `git push` 到 `main` 分支会自动重新发布。

> 注意：仓库为公开仓库，页面内的模型密钥保存在各自浏览器中，不会随仓库分发。**请勿把 API Key 写回 `index.html`**。
