<div align="center">

# 🚴‍♂️ Cycle Share Data Analysis

**レンタルサイクル利用データの可視化と分析プロジェクト**

[![Python](https://img.shields.io/badge/Python-3.12.11-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-green.svg)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-red.svg)](https://matplotlib.org/)

*データサイエンスの視点から見る都市交通の利用パターン*

</div>

---

## 📋 目次

- [プロジェクト概要](#-プロジェクト概要)
- [データセット](#-データセット)
- [機能](#-機能)
- [セットアップ](#-セットアップ)
- [使用方法](#-使用方法)
- [分析内容](#-分析内容)
- [技術スタック](#-技術スタック)
- [プロジェクト構成](#-プロジェクト構成)
- [著者](#-著者)

---

## 🎯 プロジェクト概要

このプロジェクトは、レンタルサイクルサービスの利用データを分析し、時間帯別の利用パターンやユーザー属性（登録ユーザー vs 非登録ユーザー）による利用傾向の違いを可視化・考察するデータ分析プロジェクトです。

### 主な分析ポイント

- ⏰ **時間帯別の利用パターン分析**
- 👥 **ユーザー属性による利用傾向の比較**
- 📊 **データの可視化と統計的分析**
- 🔍 **データクリーニングと前処理**

---

## 📊 データセット

### `cycle.csv`

レンタルサイクルサービスの利用データ（2011-2012年）

#### データ項目

| カラム名 | 説明 | データ型 |
|---------|------|---------|
| `instant` | レコード番号 | int |
| `dteday` | 日付 | string |
| `season` | 季節 (1:春, 2:夏, 3:秋, 4:冬) | int |
| `yr` | 年 (0: 2011, 1: 2012) | int |
| `mnth` | 月 (1～12) | int |
| `hr` | 時間 (0～23) | float |
| `holiday` | 祝日フラグ | int |
| `weekday` | 曜日 (0:日, 1:月, ..., 6:土) | int |
| `workingday` | 営業日フラグ | int |
| `weathersit` | 天気 (1:晴れ, 2:曇り, 3:雨, 4:豪雨・雪) | int |
| `temp` | 平均気温 | float |
| `atemp` | 平均体感気温 | float |
| `hum` | 平均湿度 | float |
| `windspeed` | 平均風速 | float |
| `casual` | 非登録ユーザー利用数 | int |
| `registered` | 登録ユーザー利用数 | int |
| `cnt` | 総利用数 | int |

**データ規模**: 17,379行 × 17列

---

## ✨ 機能

- ✅ CSVデータの読み込みと前処理
- ✅ 欠損値の検出と処理
- ✅ 基本統計量の算出
- ✅ 時間帯別の利用数集計
- ✅ ユーザー属性別の利用傾向分析
- ✅ 美しい可視化（棒グラフ、積み上げ棒グラフ）
- ✅ 日本語フォント対応

---

## 🚀 セットアップ

### 必要な環境

- Python 3.12.11
- pip

### インストール手順

1. **リポジトリのクローン**
```bash
git clone git@github.com:yut0takagi/ass-ds-tools-4.git
cd ass-ds-tools-4
```

2. **仮想環境の作成と有効化**
```bash
python -m venv .venv
source .venv/bin/activate  # macOS/Linux
# または
.venv\Scripts\activate  # Windows
```

3. **依存パッケージのインストール**
```bash
pip install pandas matplotlib japanize-matplotlib setuptools
```

> **注意**: Python 3.12では`distutils`が削除されているため、`setuptools`のインストールが必要です。

---

## 📖 使用方法

### Jupyter Notebookの起動

```bash
jupyter notebook notebooks/report_python_髙木悠人.ipynb
```

### 分析の実行

1. ノートブックを開く
2. セルを順番に実行
3. グラフと分析結果を確認

### 主要な分析ステップ

```python
# 1. データの読み込み
df_cycle = pd.read_csv('../cycle.csv')

# 2. 基本統計量の確認
df_cycle.describe()

# 3. 時間帯別の利用数集計
df_cycle_hr = df_cycle.groupby('hr')['cnt'].sum()

# 4. 可視化
df_cycle_hr.plot(kind='bar')
plt.show()
```

---

## 📈 分析内容

### 1. 時間帯別の利用パターン

朝（8時）と夕方（17時）に利用者数がピークを迎える傾向が確認されました。これは通勤・通学時間帯と一致しており、レンタルサイクルが日常的な移動手段として活用されていることが示唆されます。

### 2. ユーザー属性別の利用傾向

- **登録ユーザー**: 朝・夕方の通勤時間帯に加え、昼間（10-15時）にも利用が多く、日常的な移動手段として定期的に活用
- **非登録ユーザー**: 朝・夕方の通勤時間帯に集中し、一時的な利用や観光目的での利用が多い傾向

### 3. 主要な発見

🔍 **登録ユーザーはレンタルサイクルを日常的な移動手段として定期的に活用**

🔍 **非登録ユーザーは通勤・通学などの特定の時間帯に限定的に利用**

🔍 **利用目的はユーザー属性によって明確に異なる**

---

## 🛠 技術スタック

| カテゴリ | 技術 |
|---------|------|
| **言語** | Python 3.12.11 |
| **データ分析** | Pandas |
| **可視化** | Matplotlib |
| **日本語対応** | japanize-matplotlib |
| **開発環境** | Jupyter Notebook |
| **環境管理** | venv |

---

## 📁 プロジェクト構成

```
ass-ds-tools-4/
│
├── 📄 README.md                    # このファイル
├── 📊 cycle.csv                    # レンタルサイクル利用データ
├── 📁 notebooks/                   # 分析ノートブック
│   └── report_python_髙木悠人.ipynb
│
└── 📁 .venv/                       # 仮想環境（gitignore）
```

---

## 👤 著者

**髙木悠人**

- 所属: 中央大学理工学部ビジネスデータサイエンス学科
- 学籍番号: 23D7104001I

---

## 📝 ライセンス

このプロジェクトは [MIT License](LICENSE) の下で公開されています。

Copyright (c) 2024 髙木悠人

---
