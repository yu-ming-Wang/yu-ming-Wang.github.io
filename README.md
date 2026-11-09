# Yuming Wang · Portfolio

個人作品集，使用 Astro、TypeScript 與原生 CSS，產出可部署到 GitHub Pages 的靜態網站。包含手機版排版、明暗主題、專案介紹頁、SEO metadata 和 404 頁面。

## 本機開發

需要 Node.js 24 和 npm。若使用 nvm：

```bash
nvm install
nvm use
npm install
npm run dev
```

開啟終端機顯示的本機網址（預設 `http://localhost:4321`）。第一次安裝後請將產生的 `package-lock.json` 一起提交，後續安裝與 CI 即可使用 `npm ci`。

```bash
npm run build
npm run preview
```

`build` 產生 `dist/`；`preview` 預覽建置後的網站。GitHub Pages 不需要 Node.js 伺服器。

## 更新內容

- `src/data/portfolio.ts`：個人資料、聯絡方式、專案內容；填入專案的 `repository` 即可在介紹頁顯示原始碼連結。
- `src/pages/index.astro`：首頁內容與結構。
- `src/pages/projects/[slug].astro`：共用專案頁模板，新增資料項目會在建置時自動產生頁面。
- `src/styles/global.css`：配色、字型、響應式排版。
- `public/images/profile.jpg`：個人照片。
- `public/resume/yuming_wang_resume.pdf`：履歷；原本的公開網址保持可用。

教育與經歷沿用原站資料，發布前請確認仍符合現況。專案描述根據原站整理，未填入未提供的效能數字、成果或 repository 連結。

## GitHub Pages 部署

此 repo 是 `yu-ming-Wang.github.io`，因此網站位於網域根目錄，不需設定 repository 子路徑。

1. 在 GitHub 開啟 repo 的 **Settings → Pages**。
2. 將 **Build and deployment → Source** 改為 **GitHub Actions**。
3. 將本機變更提交並推送到 `main`。
4. 在 **Actions** 查看 `Deploy portfolio to GitHub Pages` 是否完成。

成功後網址為 **https://yu-ming-wang.github.io/**。PR 只進行建置檢查；推送到 `main` 或在 `main` 手動執行 workflow 才發布。

Workflow 初次沒有 lockfile 時使用 `npm install`；提交 lockfile 後會自動改用 `npm ci`。

遷移後的入口是 `src/pages/index.astro`，不再直接編輯 repo 根目錄的 `index.html`。圖片和履歷已移至 `public/`，建置後仍對應原本的 `/images/`、`/resume/` 網址。

參考：[Astro 官方 GitHub Pages 部署文件](https://docs.astro.build/en/guides/deploy/github/)。
