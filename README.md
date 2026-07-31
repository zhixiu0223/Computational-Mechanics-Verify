# 計算力學方法論——驗證、確效與跨平台交叉比對
### Computational Mechanics Methodology: Verification, Validation, and Cross-Platform Comparison

[![Open Week 1 in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/zhixiu0223/Computational-Mechanics-Verify/blob/main/notebooks/week01_1d_bar_four_methods.ipynb)
[![Notebook CI](https://github.com/zhixiu0223/Computational-Mechanics-Verify/actions/workflows/notebook-ci.yml/badge.svg)](https://github.com/zhixiu0223/Computational-Mechanics-Verify/actions/workflows/notebook-ci.yml)
[![License: MIT](https://img.shields.io/badge/code-MIT-blue.svg)](LICENSE)
[![Docs: CC BY 4.0](https://img.shields.io/badge/docs-CC%20BY%204.0-lightgrey.svg)](LICENSE)

> 這是課程開課前的公開預覽 repo。選課前你可以先看這裡的內容,判斷這門課適不適合你。
> 內容會**逐週釋出**,目前已釋出第 1、2、3 週完整教材,其餘週次會依課程進度陸續 push 上來。

---

## 這門課在教什麼

坊間大部分計算力學/有限元素課程教「怎麼用某套軟體算出答案」。
這門課反過來——**每一週給一個力學問題,要求用至少兩種理論獨立、實作獨立的方法求解,並解釋:如果兩者不一致,問題出在哪一層**(離散化?邊界條件?程式 bug?還是理論本身的極限?)。

不是工具操作課,是研究方法論課。

## 這門課不教什麼

- 不是「Abaqus/ANSYS 操作入門」
- 不是純理論推導課(前提是你已經修過材料力學/結構學)
- 不預設你要用某一套特定商用軟體——案例會刻意混用開源工具,逼你習慣「换一套工具答案會不會變」這件事

## 先修需求

- 材料力學或結構學(至少一門)
- 數值方法或工程數學(要看得懂剛度矩陣、高斯積分是什麼)
- 基礎 Python(不用很強,但要能讀懂/修改別人寫的迴圈)

適合對象:大三下/大四選修,或碩一入門選修。土木、結構、機械工程系皆可。

## 學分與時數

3 學分(2 小時講授 + 2 小時實作/週,共 18 週)

## 學習目標

- 能推導簡單力學問題的強形式與弱形式,並理解兩者等價性
- 能手動組裝有限元素矩陣(不依賴套件),並用套件結果反向驗證自己的程式碼
- 能設計交叉驗證實驗(不同理論框架、不同軟體、不同數值策略)
- 能辨識何時「結果一致」是理論保證,何時只是巧合(甚至是兩個工具共享了同一個隱藏假設)
- 養成「先寫驗證測試,再信任模型輸出」的工程習慣——包含面對 AI 生成程式碼時的驗證責任

## 評分方式(草案)

| 項目 | 比例 |
|---|---|
| 每週實作作業(交叉驗證報告) | 40% |
| 期中案例研究 | 25% |
| 期末專題(自選非線性/多維問題,完整四方比對) | 35% |

## 18 週大綱

完整版見 [`syllabus/full-syllabus.md`](syllabus/full-syllabus.md)。以下是總覽:

| 週次 | 主題 |
|---|---|
| 1 | 課程概論:為什麼「算得出來」不等於「算得對」 |
| 2 | 強形式 vs 弱形式:從 ODE 到變分原理 |
| 3 | 手算有限元素法:形狀函數、高斯積分、矩陣組裝 |
| 4 | 套件即黑箱:如何用套件反向驗證自己的程式碼 |
| 5 | 獨立驗證途徑:當 ODE 求解器與 FEM 無關卻給出相同答案代表什麼 |
| 6 | 樑元素與集中塑性鉸:當「節點精確」不再成立時怎麼辦 |
| 7 | 集中塑性 vs 纖維模型 |
| 8 | 手算驗證的極限:slope-deflection、虛功、能量法交叉檢核 |
| 9 | 期中案例研究工作坊 |
| 10 | 二階效應與 P-Delta:理論相同的工具為何仍會分歧 |
| 11 | 收斂陷阱:偽收斂與奇異矩陣 |
| 12 | 客製化元素開發導論 |
| 13 | 隱藏的非線性:求解器有沒有真的在跌代? |
| 14 | 多軸向土壤本構模型驗證 |
| 15 | CFD 驗證方法論:網格收斂性研究為什麼經常失敗 |
| 16 | 跨工具驗證的哲學:一致是證據,還是巧合? |
| 17 | 期末專題工作坊 |
| 18 | 期末專題發表 + 課程總結 |

## 已釋出教材先睹為快

**第 1 週** [`notebooks/week01_1d_bar_four_methods.ipynb`](notebooks/week01_1d_bar_four_methods.ipynb) ——
一維桿件靜力問題,四種方法(解析解 / 手算 FEM / scikit-fem 弱形式 / SciPy BVP)交叉比對。
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/zhixiu0223/Computational-Mechanics-Verify/blob/main/notebooks/week01_1d_bar_four_methods.ipynb)

**第 2 週** [`notebooks/week02_strong_weak_form.ipynb`](notebooks/week02_strong_weak_form.ipynb) ——
從統御方程式正式推導強形式與弱形式的等價性,並把第 1 週的常係數桿件推廣成變係數 $EA(x)$,
示範「節點精確性」為何在更一般的問題中會失效。
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/zhixiu0223/Computational-Mechanics-Verify/blob/main/notebooks/week02_strong_weak_form.ipynb)

**第 3 週** [`notebooks/week03_convergence_rate.ipynb`](notebooks/week03_convergence_rate.ipynb) ——
手算收斂率分析:延續第 2 週的變係數桿件,手動推導並實作二次(P2)元素,系統性地把元素數量
從 2 掃到 64,量測 $L^2$/能量範數誤差的收斂階數,並與理論預期(P1: 2/1 階,P2: 3/2 階)比對;
同時用 scikit-fem 的 `ElementLineP2` 反向驗證手算 P2 元素的正確性。
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/zhixiu0223/Computational-Mechanics-Verify/blob/main/notebooks/week03_convergence_rate.ipynb)

點徽章可以直接在瀏覽器打開跑一次,不用裝環境。

## 本 repo 如何成長

這個 repo 是**逐週建構**的,不是一次性上傳完整課程。commit 歷史本身就是課程開發過程的紀錄:

```
git log --oneline
```

會看到每一週教材、每一次教學設計調整,都是獨立、有意義的 commit——這也呼應課程本身的精神:**留下可追溯、可驗證的過程紀錄**,而不是只交出一個看起來對的最終結果。

## 環境設置

```bash
pip install -r requirements.txt
jupyter notebook notebooks/
```

或直接點 Colab 徽章,不用本機裝任何東西。

## 授課教師

課程綱要與教材規劃中,歡迎透過 Issues 提問或提出案例建議。
