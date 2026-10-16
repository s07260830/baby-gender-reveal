# Baby Gender Reveal — 10 題即時遊戲

## 三個入口
- `player.html`：賓客
- `host.html`：主持人（Email/Password 登入）
- `screen.html`：投影

## Firebase 設定
1. 到 https://console.firebase.google.com 建立 Firebase 專案。
2. Build → Realtime Database → 建立資料庫，記下 databaseURL。
3. Project settings → Your apps → Add Web app，複製 `firebaseConfig` 的 `apiKey`、`authDomain`、`databaseURL`、`projectId`、`appId` 到 `config.js`。
4. Authentication → Sign-in method → 啟用 Email/Password；Users → Add user 建立主持人帳密。
5. Realtime Database → Rules → 貼上 `database.rules.json` 內容並 Publish。
6. Authentication → Settings → Authorized domains → 新增 `s07260830.github.io`（若使用該網域）。

**重要：** 此版是小型私人活動 MVP，資料庫規則讓未登入賓客能寫入遊戲投票，但無法嚴格防止冒名修改其他人的投票，也讓投影頁可讀暱稱。請勿收集敏感資訊或將連結公開廣傳。正式活動建議加入 Firebase Anonymous Authentication、每人獨立 UID 及更嚴格的權限驗證。

## GitHub Pages
1. 建立公開 Repository `baby-gender-reveal`，上傳這個資料夾的所有檔案至 repo 根目錄。
2. Settings → Pages → Deploy from a branch → main / (root) → Save。
3. 等待 Pages 建置成功後使用：
   - `https://s07260830.github.io/baby-gender-reveal/player.html`
   - `https://s07260830.github.io/baby-gender-reveal/host.html`
   - `https://s07260830.github.io/baby-gender-reveal/screen.html`
4. 先用兩台手機測試；主持人推進題目，另一台開投影確認同步。

## 使用限制
- 主持人只有一個；多主持人同時按下一步可能衝突。
- 目前賓客身分存在瀏覽器 localStorage，清除瀏覽資料會失去原身分。
- 本版未附 QR 圖片；部署後可用實際 player URL 產生 QR Code。
- 第 10 題鎖定最終戰隊直接揭曉男寶。
