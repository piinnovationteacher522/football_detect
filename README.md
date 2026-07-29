# 足球偵測 × micro:bit

用自訓練嘅 Edge Impulse FOMO 模型偵測足球，畫框跟蹤，並經藍牙將 XY 座標傳去 micro:bit。

## 上載去 GitHub Pages

### 1. 開新 repo

去 github.com → 右上角 **+** → **New repository**

| 設定 | 值 |
|---|---|
| Repository name | `football-tracker` |
| Visibility | **Public** ⚠️ 免費帳戶必須公開 |
| Add a README file | **唔好剔**（呢度已經有） |

撳 **Create repository**。

### 2. 上載檔案

喺新 repo 頁面撳 **uploading an existing file**（或 Add file → Upload files）。

將呢五個檔案**一齊拖入去**：

```
index.html                      ← 主程式
edge-impulse-standalone.js      ← Edge Impulse 載入器
edge-impulse-standalone.wasm    ← 你嘅 FOMO 模型（8.2 MB）
server.py                       ← 本機測試用（GitHub 上唔會用到）
.nojekyll                       ← 叫 GitHub 唔好處理檔案
README.md                       ← 呢份說明
```

> **`.nojekyll` 睇唔到？** 佢係隱藏檔案。
> Mac 喺 Finder 撳 `Cmd + Shift + .` 顯示隱藏檔案；
> Windows 喺檔案總管 → 檢視 → 剔「隱藏的項目」。
> 其實呢個 project 冇 `_` 開頭嘅檔案，唔加都行得。

撳 **Commit changes**。

> 8.2 MB 嘅 wasm 冇問題 —— 網頁上載上限係每個檔案 25 MB。

### 3. 開啟 Pages

**Settings** → 左邊選單 **Pages** →

| 設定 | 值 |
|---|---|
| Source | Deploy from a branch |
| Branch | `main` |
| Folder | `/ (root)` |

撳 **Save**，等 1～2 分鐘。

### 4. 開網址

```
https://你嘅帳戶名.github.io/football-tracker/
```

用 **Chrome** 開。因為係 `https://`，鏡頭同 Web Bluetooth 都用得。

---

## 常見問題

**模型載入失敗 / 一直 COCO-SSD**
`.wasm` 冇上載成功。返 repo 睇下三個檔案齊唔齊、檔名有冇改過。

**第一次開好慢**
要下載 8.2 MB 模型，正常。之後瀏覽器會快取，秒開。
想細啲：返 Edge Impulse 嘅 Deployment，開埋 **EON Compiler** 再 Build 一次。

**改完嘢個網頁冇更新**
GitHub Pages 有快取。等 1～2 分鐘，再撳 `Ctrl + Shift + R`（Mac：`Cmd + Shift + R`）強制重新載入。

**404**
Pages 未 build 好（等耐啲），或者主檔案唔叫 `index.html`。

**iPad 藍牙連唔到**
iPadOS 嘅 Safari / Chrome 都唔支援 Web Bluetooth。
去 App Store 裝 **Bluefy**，用佢開同一條 https 網址就得。鏡頭同 AI 偵測喺 Safari 本身冇問題。

---

## 更新檔案

改完 `index.html` 之後：repo → 揀個檔案 → 鉛筆圖示 → 貼上新內容 → Commit。
或者用 Add file → Upload files 覆蓋。

---

## 注意

Public repo 即係人人睇到你嘅程式碼同模型檔案。
呢個 project 冇密碼、冇個人資料，公開冇問題。
但**唔好**喺入面放 API key、密碼或者私人相片。
