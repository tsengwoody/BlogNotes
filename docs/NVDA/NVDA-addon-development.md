# NVDA addon 開發小心得

[[toc]]

## 先備能力

想開發 NVDA addon 前需先熟悉 NVDA 操作與 python3

*	addon 就是要來加強 NVDA 的功能，不會操作就不知道有什麼需改善或客製化的目標，想當然不知從何下手
*	不會操作連做好的程式都無法執行並測試
*	於 2019.3 後的 NVDA 已改用 python 3.7 開發且python 2 於 2020 年 1 月 停止支援了，故要入門就直接學 python3 吧

## 建立基本概念

有了以上兩項先備能力後就可以逐步看官方或社群的一些文件了

以下列出想開發 addon 的建議閱讀文章順序

*	[NVDA Developer Guide](https://www.nvaccess.org/files/nvda/documentation/developerGuide.html):這篇非常的基礎，介紹了簡單的 addon 概念
*	[NVDA Add-on Development Guide](https://github.com/nvdaaddons/DevGuide/wiki/NVDA-Add-on-Development-Guide):進皆且完整的介紹了當前開發 addon 的知識。我沒全看完，只挑了我覺得會用到的部份看，之後有需求再回頭看其他的部份。。建議可先看到 Getting started: Hands-on examples 的 2 級大標結束，其餘就試依自己想開發的 addon 功能再挑著看，或是寫久了想了解更多可能開發的功能再慢慢看即可，快速的有了基本概念後就動手實做累積經驗更重要。

## 開發準備

動手實做前照著官方建議的 [AddonTemplate](https://github.com/nvdaaddons/AddonTemplate) 建個環境吧

*	下載 [Python 3.7](https://www.python.org/ftp/python/3.7.5/python-3.7.5.exe) 安裝。未來進階要 build NVDA 原始碼亦是需要 32 bit 版
*	> pip install markdown
*	下載 [Scons](https://www.twvip.org/scons-3.0.0-setup.exe) 安裝。(用 pip 安裝無法在 CMD 下 scons 指令，可能我環境沒正確設定，故用 exe 安裝)
*	下載 [Git](https://git-scm.com/download/win) 安裝

## 開發流程

以上就建立好了專案的環境，可以實際開始開發程式了。

當你開發完成後，可執行以下指令來產生 .nvda-addon 與 .pot 檔

*	>scons # 產生 addon
*	>scons pot # 產生 .pot 翻譯檔

有了 .nvda-addon 檔就能按裝到 NVDA 內來執行了。

### 快速測試

以上方式當每次修改完成就需產生 .nvda-addon 檔在安裝到 NVDA 內測試其實有點麻煩，當在開發階段建議可直接將專案目錄下的 addon 資料夾複製到 NVDA使用者目錄\addons 內。

此後，當修改了一些內容後可直接按 NVDA+ctrl+F3 來重新載入 addon 來確認修改後的程式行為。

等到整個都開發完再複製回專案目錄並產生 .nvda-addon 檔即可。

## 動手實做

當你讀完教學文件並完成以上準備後，就發揮你的創意與觀察發覺不便處擬訂想解決的問題，不論多麼微小的功能都沒關系，先試著做點什麼感受編寫 addon 的魅力吧。

逐步的若想開發更複雜的功能建議從觀摩其他人的程式開始，找個有興趣的 NVDA 功能或 addon 去 trace code 涉法找到該功能原始碼來學習。

從 trace code 來了解實現功能的方法，在這過程中一定會遇到一堆看不懂的 python 語法或 API 一關一關的去了解克服打好基礎，最終就可以開發出實用的功能。

最後讀了一段時間的原始碼想完整建立 NVDA 架構概念再看 [DesignOverview](https://github.com/nvaccess/nvda/wiki/DesignOverview) 與 [internals](https://github.com/nvaccess/nvda-community/wiki/internals) 的內容

以上大致是我學習的方法、步驟與建議供大家參考。
