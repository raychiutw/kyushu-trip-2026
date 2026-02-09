# CLAUDE.md

此檔案為 Claude Code (claude.ai/code) 在本專案中運作時的指引。

## 專案概述

這是一個單檔靜態 HTML 旅遊行程表，規劃 2026 年 2 月 16-22 日的九州七天家庭自駕旅行（2 大 2 小）。內容以繁體中文（zh-TW）撰寫。

## 架構

整個專案僅有一個 `index.html` 檔案（約 2000 行），無建置系統、無外部相依套件、無 JavaScript。所有 CSS 皆內嵌於 `<style>` 區塊中，可直接於瀏覽器開啟。

### HTML 結構（依序排列）

1. **CSS 變數與樣式**（約第 1-311 行）— 以 CSS 自訂屬性定義主題色彩（`--sky-blue`、`--warm-brown` 等），響應式版面配置，行動裝置斷點為 600px
2. **頁首** — 旅行標題、路線摘要、出發地點
3. **出發前確認事項** — 旅行前需確認的項目（火山狀態、天氣、訂位）
4. **航班資訊** — 去程（TPE→KMJ）與回程（FUK→TPE）
5. **每日行程卡片（Day 1-7）** — 每日包含：日期標題（漸層色）、天氣資訊、住宿資訊、時間軸行程與時段、景點間交通方式、預算估計、備註
6. **雨天備案** — 各日的下雨替代方案
7. **緊急聯絡資訊** — 重要電話與地址
8. **頁尾** — 旅程總結與總預算估計

### 重要 CSS 模式

- 每日（1-7）各有獨立配色，透過 `.day-N` class 套用（標題漸層、時間標籤、卡片邊框）
- 景點間交通指示使用 `.transport-line` 搭配修飾類別：`.drive`、`.walk`、`.train`
- 行程分類標籤：`.tag-food`、`.tag-attraction`、`.tag-shopping`、`.tag-nature`、`.tag-reservation`、`.tag-transport`
- 預約/訂位提醒使用 `.reservation-info`（紅色）與 `.parking-info`（綠色）
- 付款狀態標籤：`.status-paid`（綠色）與 `.status-pending`（橘色）

## 開發方式

無需建置步驟。直接於瀏覽器開啟 `index.html` 即可預覽。Windows 上可執行：

```
start index.html
```

## 慣例

- 所有行程內容使用繁體中文
- 餐廳與景點名稱應盡量使用日文原名
- Google Maps 連結以 `.map-link` 元素嵌入，指向 `maps.google.com/?q=`
- 外部連結（飯店、餐廳、景點）以新分頁開啟（`target="_blank"`）
- 預算表格使用日圓（¥）並附台幣（NT$）換算
