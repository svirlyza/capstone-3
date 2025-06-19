# capstone-3
# Travel Insurance Claim Classification
Capstone Project – Purwadhika Data Science Bootcamp  
Author: **Shatara Virlyza**

## Project Introduction

Perusahaan asuransi perjalanan menghadapi tantangan dalam mengidentifikasi pelanggan yang berisiko tinggi untuk mengajukan klaim. Dari data historis, hanya sekitar 1% pelanggan yang benar-benar melakukan klaim. Oleh karena itu, proyek ini bertujuan untuk membangun model klasifikasi yang mampu mengenali pelanggan yang cenderung mengajukan klaim asuransi perjalanan, dengan mempertimbangkan ketidakseimbangan data.

## Business Objective

- Mengembangkan model klasifikasi prediktif untuk mendeteksi potensi klaim.
- Meminimalkan False Negative (FN) dengan mengutamakan **F2-score** sebagai metrik utama.
- Mengidentifikasi fitur yang paling berkontribusi terhadap prediksi.
- Memberikan interpretasi model yang transparan menggunakan SHAP & LIME.

## Dataset

- **Sumber**: Kaggle – [Travel Insurance Dataset](https://www.kaggle.com/datasets/mhdzahier/travel-insurance/data)
- **Jumlah data**: ± 56.000 baris
- **Target**: Kolom `Claim` (Yes/No)

### Fitur utama:
- Demografi: `Age`, `Gender`, `Destination`
- Transaksi: `Net Sales`, `Commision (in value)`
- Produk: `Product Name`, `Agency`, `Distribution Channel`

## Modeling Pipeline

1. **Preprocessing**:
   - Drop kolom `Gender` (missing >50%)
   - RobustScaler untuk fitur numerik
   - OneHotEncoder untuk fitur kategorikal
2. **Handling Imbalance**:
   - Menggunakan **RandomUnderSampler** dan **NearMiss**
3. **Modeling**:
   - Logistic Regression (`class_weight=balanced`)
   - KNN
   - Random Forest
4. **Model Selection**:
   - Menggunakan **cross-validation** (`StratifiedKFold`)
   - Metrik utama: **F2-score**

## Best Model

| Model               | Sampler         | F2 Score (Test) |
|---------------------|------------------|------------------|
| Logistic Regression | RandomUnderSampler | **0.234**        |

## Explainability

- **SHAP** digunakan untuk analisis global dan lokal pentingnya fitur.
- **LIME** digunakan untuk menjelaskan keputusan model terhadap prediksi individual pelanggan.

## Files

- `Capstone_3.ipynb` : Notebook lengkap proses EDA, preprocessing, modeling, dan interpretasi.
- `logreg_randomunder.pkl` : File model terbaik (Logistic Regression + RandomUnderSampler) yang telah disimpan menggunakan Pickle.
- `README.md` : Dokumentasi dan penjelasan proyek.

## Insights & Recommendation

- Produk seperti `Cancellation Plan`, agen tertentu (`EPX`), serta destinasi (`THAILAND`) berkontribusi tinggi terhadap klaim.
- Model memberikan recall tinggi untuk pelanggan yang melakukan klaim, sesuai dengan tujuan bisnis.
- Rekomendasi untuk tim underwriting dan marketing agar fokus pada segmen pelanggan berisiko tinggi dan evaluasi ulang produk dengan potensi klaim tinggi.
