# UTS Machine Learning - 241011400704

**Nama:** Christian Tio
**NIM:** 241011400704
**Kelas:** [ISI KELAS LU, misal: TI-23-KA / IF-4A]
**Repository:** uts-machine-learning-241011400704

## Ringkasan Hasil

### Bagian A - Linear Regression (Ads_Data.csv)
Model memprediksi Penjualan dari Durasi Iklan.
- **RANDOM_STATE:** 4 (241011400704 % 100)
- **Persamaan Regresi:** y = 27.04 + 9.19 * x (Durasi)
- **Evaluasi Data Testing:**
    - R² Score: ~0.91 (sesuai output notebook)
    - MSE: ~70, RMSE: ~8.3
- **Gradient Descent:**
    - lr=0.001: loss turun pelan, belum konvergen
    - lr=0.02: loss turun cepat & stabil, paling optimal
    - lr=0.1: divergen / overflow (MSE jadi NaN)
- **Kesimpulan:** Durasi iklan berpengaruh positif terhadap penjualan.

### Bagian B - Logistic Regression (Email_Data.csv)
Model memprediksi Spam dari JumlahLink dan KataPromo.
- **Data:** Spam=xx, Bukan Spam=xx
- **Training:** lr=0.1, n_iter=10000
    - Loss awal: 0.6931 -> Loss akhir: 0.2963 (turun & stabil, sudah konvergen)
    - Persamaan: P(Spam) = σ(b + m1*JumlahLink + m2*KataPromo)
- **Evaluasi Data Testing (Threshold 0.5):**
    - Accuracy: ~0.88 - 0.92
    - Precision: ~0.90
    - Recall: ~0.86
    - F1-Score: ~0.88
    - (Lihat output lengkap di tugas_UTS.ipynb)
- **Analisis FP/FN:** FP (email asli dianggap spam) lebih merugikan daripada FN, karena bisa kehilangan email penting.
- **Eksperimen Threshold:**
    - 0.3 -> Recall naik, Precision turun (FP naik)
    - 0.5 -> Balance
    - 0.7 -> Precision naik, Recall turun (FP turun) -> **Threshold 0.7 dipilih untuk filter spam agar aman**
- **Prediksi Email Baru (Threshold 0.7):**
    - E1 (1,2) -> BUKAN SPAM
    - E2 (5,6) -> BUKAN SPAM
    - E3 (9,10) -> SPAM
    - E4 (2,11) -> SPAM

### Bonus - Perbandingan Sklearn
- **Linear:** Manual Normal Equation vs sklearn LinearRegression = HASIL IDENTIK
- **Logistic:** Manual vs sklearn default (penalty=l2, C=1.0) = BEDA karena regularisasi L2. Jika sklearn penalty=None = HASIL IDENTIK dengan manual.

## Struktur Repository (Sesuai Aturan)