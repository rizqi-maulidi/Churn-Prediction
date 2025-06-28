# Laporan Proyek Churn Prediction - Rizqi Maulidi

## Domain Proyek

Seiring dengan pesatnya perkembangan industri telekomunikasi, perusahaan penyedia layanan dihadapkan pada tantangan untuk tidak hanya memperluas basis pelanggan, tetapi juga mempertahankan pelanggan yang sudah ada. Dalam iklim persaingan yang semakin ketat, menjaga loyalitas pelanggan menjadi prioritas utama, mengingat biaya untuk mendapatkan pelanggan baru jauh lebih tinggi dibandingkan biaya mempertahankan pelanggan yang ada.

Kehilangan pelanggan (customer churn) dapat berdampak signifikan terhadap pendapatan dan stabilitas perusahaan dalam jangka panjang. Oleh karena itu, penting bagi perusahaan telekomunikasi untuk memahami perilaku konsumen secara mendalam dan memanfaatkan predictive analytics guna mengidentifikasi pelanggan yang berisiko tinggi untuk churn. Dengan pendekatan ini, perusahaan dapat merancang strategi retensi yang lebih tepat sasaran.

Dalam proyek ini, digunakan data pelanggan dari sebuah perusahaan telekomunikasi, yang mencakup berbagai atribut terkait layanan yang digunakan oleh masing-masing pelanggan. Melalui analisis data ini, diharapkan dapat ditemukan variabel-variabel yang berkontribusi terhadap churn, memprediksi pelanggan yang kemungkinan besar akan berhenti berlangganan, serta mengusulkan tindakan preventif untuk mengurangi tingkat churn.


### Mengapa Masalah Ini Harus Diselesaikan?

Masalah *churn* pelanggan di industri telekomunikasi sangat krusial karena kehilangan pelanggan secara langsung berdampak pada pendapatan perusahaan.

- Studi industri menunjukkan bahwa biaya untuk mendapatkan pelanggan baru bisa 5 hingga 7 kali lebih mahal daripada mempertahankan pelanggan yang sudah ada.
- Tingginya tingkat *churn* juga dapat merusak reputasi perusahaan, memperlambat pertumbuhan bisnis, dan meningkatkan biaya operasional.

Solusinya adalah dengan *predictive analytics*, yaitu:

- Menganalisis data historis pelanggan.
- Membangun model machine learning untuk memprediksi kemungkinan *churn*.
- Mengidentifikasi faktor utama penyebab *churn*.
- Membuat strategi retensi seperti promo khusus atau peningkatan layanan.
- Memonitor hasil dan memperbaiki strategi berdasarkan data.

### Referensi
- Menyertakan hasil riset terkait atau referensi. Referensi yang diberikan harus berasal dari sumber yang kredibel dan author yang jelas.
  
  Format Referensi: [Comparing to Techniques Used in Customer Churn Analysis](https://www.researchgate.net/profile/Oezer-Celik-2/publication/337103029_Comparing_to_Techniques_Used_in_Customer_Churn_Analysis/links/5dc52a29a6fdcc2d2ffc1a24/Comparing-to-Techniques-Used-in-Customer-Churn-Analysis.pdf) 

## Business Understanding

Pada bagian ini menjelaskan proses klarifikasi masalah.

### Problem Statements

- Bagaimana mengidentifikasi pelanggan yang berpotensi tinggi untuk melakukan churn?
Banyak pelanggan berhenti berlangganan tanpa terdeteksi lebih awal, menyebabkan perusahaan kehilangan pendapatan secara signifikan.
- Faktor apa saja yang paling berkontribusi terhadap churn pelanggan?
Tanpa mengetahui faktor utama penyebab churn, perusahaan sulit menentukan tindakan yang efektif untuk mempertahankan pelanggan.

### Goals

- Membangun model prediksi churn pelanggan
Membuat model machine learning yang mampu mengklasifikasikan pelanggan berdasarkan kemungkinan churn, sehingga perusahaan dapat mendeteksi risiko sejak dini.
- Mengidentifikasi faktor-faktor utama yang mempengaruhi churn
Menentukan variabel-variabel penting (seperti penggunaan layanan, biaya, aktivitas kontrak) yang berkorelasi kuat dengan churn, untuk mendukung analisis bisnis.



### Solution statements
- Membangun dan Membandingkan Beberapa Model Machine Learning
Untuk mencapai tujuan prediksi churn yang akurat, akan dibangun dan dibandingkan beberapa algoritma klasifikasi, seperti: Logistic Regression, Random Forest, XGBoost. Setiap model akan diukur performanya menggunakan metrik evaluasi seperti Accuracy (tingkat ketepatan klasifikasi), Precision, Recall, dan F1-Score (karena churn adalah masalah yang sensitif terhadap kesalahan klasifikasi), ROC-AUC (untuk mengukur kemampuan model membedakan pelanggan churn dan tidak churn) dan Melakukan Hyperparameter Tuning untuk Model Terbaik Tujuannya adalah untuk meningkatkan skor evaluasi, Mengurangi overfitting atau underfitting, Menemukan kombinasi parameter yang optimal untuk prediksi churn.

- Menggunakan Feature Selection untuk Meningkatkan Kinerja Model
Dilakukan pemilihan fitur berdasarkan importance scores (misal dari Random Forest atau XGBoost) untuk menghilangkan fitur yang tidak relevan atau redundan, menyederhanakan model agar lebih cepat dan mudah diinterpretasi, meningkatkan performa model dengan hanya menggunakan fitur penting.

## Data Understanding
Pada proyek ini, data yang digunakan berasal dari Kaggle dan dapat diakses melalui tautan berikut:
Customer Churn Dataset - Kaggle. Contoh: [UCI Machine Learning Repository](https://www.kaggle.com/datasets/barun2104/telecom-churn).

Dataset ini berisi informasi pelanggan dari sebuah perusahaan telekomunikasi, dengan berbagai atribut terkait layanan yang digunakan, pola penggunaan, dan status churn pelanggan. Data ini bertujuan untuk membantu dalam membangun model prediksi churn dan menganalisis faktor-faktor yang berpengaruh terhadap keputusan pelanggan untuk tetap berlangganan atau berhenti. Dataset yang digunakan terdiri dari 3.333 baris data dan 11 kolom fitur, yang seluruhnya bertipe numerik (baik integer maupun float). 

### Variabel-variabel pada dataset Telecom Churn adalah sebagai berikut:
- Churn : Label target, menunjukkan apakah pelanggan melakukan churn (1) atau tidak (0).
- AccountWeeks : Lama waktu pelanggan telah menggunakan layanan (dalam minggu).
- ContractRenewal : Indikator apakah pelanggan memperbarui kontraknya atau tidak (1 = ya, 0 = tidak).
- DataPlan : Status apakah pelanggan memiliki paket data (1 = ya, 0 = tidak).
- DataUsage : Jumlah penggunaan data pelanggan (biasanya dalam satuan GB atau MB).
- CustServCalls : Jumlah total panggilan yang dilakukan pelanggan ke layanan pelanggan.
- DayMins : Total menit penggunaan telepon pada siang hari.
- DayCalls : Jumlah panggilan telepon yang dilakukan pada siang hari.
- MonthlyCharge : Total biaya bulanan yang harus dibayarkan pelanggan.
- OverageFee : Biaya tambahan yang dikenakan jika pelanggan melebihi batas layanan.
- RoamMins : Total menit penggunaan telepon saat pelanggan dalam kondisi roaming.

**Exploratory Data Analysis (EDA)**:
- Beberapa tahapan yang dilakukan sebagai langkah awal memahami data, dilakukan beberapa analisis eksploratori sederhana:
1. Mengecek missing value dan duplikasi 
   Berdasarkan hasil pemeriksaan, tidak terdapat nilai yang hilang (missing values) di seluruh kolom, sehingga tidak diperlukan proses imputasi atau pembersihan data terkait kekosongan nilai. Selain itu, 
   pemeriksaan terhadap duplikasi menunjukkan bahwa tidak ada baris yang terduplikasi dalam dataset ini.Secara keseluruhan, dataset ini sudah sangat layak untuk diproses ke tahap berikutnya tanpa perlu 
   penanganan khusus terhadap data yang hilang atau duplikat.
2. Distribusi Target (Churn)
   Dari hasil visualisasi mayoritas pelanggan berada pada kategori tidak churn (label 0), dengan jumlah mendekati 2.800 pelanggan. Sementara itu, hanya sekitar 500 pelanggan yang termasuk dalam kategori churn 
   (label 1). Hal ini menunjukkan bahwa data bersifat imbalanced, oleh karena itu saya melakukan pengananan untuk membuat data seimbang pada tahap data preparation.
3. Korelasi Antar Fitur
   Analisis korelasi menunjukkan bahwa terdapat hubungan sangat tinggi antara beberapa fitur, seperti antara DataPlan dan DataUsage (0.95), MonthlyCharge dan DataUsage (0.78), serta MonthlyCharge dan DataPlan 
   (0.74), yang berpotensi menimbulkan multikolinearitas dalam model linier; namun karena model yang digunakan bersifat non-linear seperti Random Forest atau XGBoost, maka korelasi antar fitur ini masih dapat 
   ditoleransi dan tidak perlu dilakukan penghapusan kolom. Selain itu, ditemukan juga beberapa fitur yang memiliki korelasi signifikan terhadap target Churn, yaitu ContractRenewal (-0.26) yang menunjukkan 
   semakin sering pelanggan memperpanjang kontrak maka semakin kecil kemungkinan mereka melakukan churn, CustServCalls (0.21) yang mengindikasikan semakin banyak pelanggan menghubungi layanan pelanggan maka 
   semakin besar kemungkinan mereka churn, serta DayMins (0.21) yang menunjukkan bahwa pelanggan dengan penggunaan telepon tinggi di siang hari cenderung memiliki kemungkinan churn yang lebih besar, mungkin 
   karena beban biaya yang tinggi.
4. Distribusi Fitur Numerik
   Secara keseluruhan, sebagian besar fitur sudah berada dalam bentuk yang cukup baik untuk digunakan dalam proses machine learning, dengan beberapa pengecualian yang memerlukan perhatian khusus terkait 
   distribusi dan potensi outlier. Sementara itu, distribusi DataUsage bersifat right-skewed atau condong ke kanan. Kondisi ini mengindikasikan adanya kemungkinan outlier, sehingga perlu dilakukan penanganan 
   lebih lanjut seperti scaling atau transformasi logaritmik untuk meningkatkan kinerja model.
5. Outlier Detection
   Dari hasil visualisasi boxplot terlihat bahwa sebagian besar nilai DataUsage berada pada rentang yang wajar, namun terdapat beberapa titik data yang berada jauh di atas batas atas (upper whisker), yang 
   ditandai sebagai outlier. Oleh karena itu saya menangani dengan teknik seperti scaling pada tahap data preparation agar tidak menghambat performa model.

## Data Preparation
1. **Menangani Missing Values dan Duplikasi**  
   Karena pada tahap EDA tidak ditemukan nilai kosong dan duplikasi jadi dataset sudah tidak perlu penanganan untuk kasus ini.

2. **Menangani outlier dengan IQR**
   Pada tahap ini fitur yang memiliki outlier seperti **DataUsage** dilakukan pengananan outlier dengan IQR.

3. **Feature Scaling**  
   Scaling dilakukan pada fitur numerik dengan StandardScaler agar semua fitur berada pada skala yang sama, agar model dapat belajar dengan baik.

4. **Membagi Data**  
   Dataset dibagi menjadi data latih dan uji (80:20) dengan stratifikasi terhadap variabel target (`Churn`) untuk menjaga proporsi kelas.

5. **Menangani Kelas Tidak Seimbang**  
   Penanganan kelas tidak seimbang agar model dapat belajar dengan baik. saya menggunakan SMOTE yang digunakan untuk menyeimbangkan dataset yang memiliki distribusi kelas yang tidak seimbang dengan cara membuat 
   data sintetis (tiruan) untuk kelas minoritas, sehingga model dapat dilatih dengan data yang lebih representatif.

6. **Menghitung VIF**  
   Nilai VIF yang tinggi biasanya menyebabkan multikoleniaritas namun karena model yang saya gunakan adalah non-linier maka saya memutuskan untuk tidak membuang fitur tersebut, alasan saya karena dikhawatirkan 
   mengurangi informasi pembelajaran model.

# 📊 Customer Churn Prediction: Modeling & Evaluation

## 🧠 Modeling

Pada tahap ini, dilakukan proses pembangunan model machine learning untuk memprediksi kemungkinan pelanggan melakukan **churn** berdasarkan fitur-fitur yang telah diproses sebelumnya.

### 1. Model yang Digunakan
Saya menggunakan **dua algoritma klasifikasi**:

- **Logistic Regression**  
- **Random Forest Classifier**

Alasan memilih kedua model ini:
- **Random Forest** adalah algoritma berbasis ensemble learning (gabungan banyak model), yang menggunakan banyak Decision Tree (pohon keputusan).
  - Cara kerjanya:
      - Bootstrap Sampling (Bagging), Dari dataset asli, Random Forest membuat beberapa subset data secara acak (dengan pengembalian – bootstrap).
      - Pohon Keputusan (Decision Trees), Untuk tiap subset data, dibuat pohon keputusan. Tiap pohon hanya “melihat” sebagian data dan sebagian fitur (random subset of features).
      - Voting / Averaging, Klasifikasi:
        - Voting mayoritas (tiap pohon “memilih” label, dan yang paling banyak dipilih jadi output akhir).
        - Regresi: Rata-rata nilai prediksi dari semua pohon.
  - Oleh karena itu saya memilih Random Forest kerana merupakan model ensemble yang kuat dalam menangani non-linearitas dan interaksi fitur.

- **XGBoost** adalah algoritma berbasis boosting, yang meningkatkan prediksi model secara iteratif.
    - Cara kerjanya:
        - Model Awal : Mulai dari model yang sederhana (bisa prediksi rata-rata, atau pohon kecil).
        - Iterasi (Additive) : Tiap langkah, tambahkan pohon keputusan baru yang mempelajari sisa error (residual) dari model sebelumnya yang “difokuskan” untuk memperbaiki kesalahan prediksi dari langkah     
          sebelumnya.
        - Gradient Descent : XGBoost menghitung gradien error untuk tiap data poin – inilah yang digunakan untuk memperbaiki model di iterasi berikutnya (mirip prinsip “turunan” di optimisasi).
        - Regularisasi & Pruning : XGBoost menambahkan regularisasi (contohnya L1, L2) untuk mencegah overfitting, dan pruning pohon yang terlalu kompleks.
    - Oleh karena itu saya memilih XGBoost karena merupakan model boosting yang efisien, powerful, dan sering memberikan hasil terbaik dalam kompetisi machine learning.


### 2. Proses Modeling

#### ✅ Model 1: Random Forest
- **Kelebihan**:
  - Dapat menangani data non-linear
  - Robust terhadap outlier dan multikolinearitas
  - Memberikan feature importance
- **Kekurangan**:
  - Lebih kompleks dan membutuhkan tuning
  - Kurang interpretatif dibanding logistic regression

#### ✅ Model 2: XGBoost
- **Kelebihan**:
  - Sangat akurat dan efisien
  - Menangani missing value secara internal
  - Mendukung regularisasi untuk mencegah overfitting
- **Kekurangan**:
  - Kompleksitas model lebih tinggi
  - Perlu tuning hyperparameter agar optimal

#### 🔧 Hyperparameter Tuning (GridSearchCV)
Dilakukan pencarian hyperparameter terbaik untuk **Random Forest** dan **XGBoost** dengan parameter berikut:

**Random Forest:**
- **Parameter default:**
  - n_estimators=100 (default): Jumlah pohon di dalam hutan (100 pohon).
  - max_depth=None (default): Kedalaman maksimum pohon; None berarti pohon akan tumbuh sampai semua daun bersih (pure).
  - random_state=42: Untuk reproduktibilitas (hasil selalu sama setiap run).
- **Hyperparameter tuning menggunakan GridSearchCV:**
  - **Parameter yang diuji:**
    - n_estimators: [100, 200] → untuk membandingkan jumlah pohon (semakin banyak bisa lebih akurat, tapi lebih lambat).
    - max_depth: [None, 10, 20] → untuk melihat apakah kedalaman terbatas lebih baik (untuk menghindari overfitting).
  - **Best Parameters setelah tuning:**
    - n_estimators=200: Menggunakan 200 pohon → meningkatkan stabilitas model.
    - max_depth=20: Batasi kedalaman hingga 20 → mencegah overfitting (jika terlalu dalam, pohon bisa hapal data train).
    - random_state=42: Sama, agar hasil tetap konsisten.

**XGBoost:**
- **Parameter default:**
  - use_label_encoder=False: Hindari warning yang muncul di versi baru XGBoost.
  - eval_metric='logloss': Gunakan log-loss sebagai metrik evaluasi (sesuai klasifikasi biner).
  - random_state=42: Untuk konsistensi hasil.
- **Hyperparameter tuning menggunakan GridSearchCV:**
  - **Parameter yang diuji:**
    - n_estimators: [100, 200] → jumlah boosting rounds.
    - max_depth: [3, 5, 7] → kedalaman maksimum pohon (semakin dalam, semakin kompleks model).
    - learning_rate: [0.01, 0.1, 0.2] → kecepatan pembelajaran (semakin kecil, lebih lambat & stabil).
    - subsample: [0.8, 1.0] → proporsi sampel yang digunakan untuk tiap pohon (1.0 = semua data, 0.8 = 80% → mencegah overfitting).
  - **Best Parameters setelah tuning:**
    - n_estimators=200: Model dilatih 200 kali boosting rounds.
    - max_depth=7: Pohon lebih dalam dari default (biasanya default 6), agar model cukup fleksibel.
    - learning_rate=0.2: Lebih tinggi dari default 0.1, supaya konvergensi lebih cepat.
    - subsample=1.0: Pakai semua data (penuh) untuk setiap pohon.
    - random_state=42: Konsistensi hasil.
### 3. Model Terbaik: Tuned XGBoost
Model ini dipilih sebagai solusi akhir karena memberikan performa paling seimbang dan unggul pada kelas minoritas (churn = 1) dibandingkan model lainnya.

---

## 📈 Evaluation

### 1. Metrik yang Digunakan
Untuk mengevaluasi performa model klasifikasi, digunakan metrik berikut:

# Rumus Metrik Evaluasi Model Churn Prediction

| Metrik | Penjelasan Singkat | Rumus |
|------------|-------------------------------------------------------------------------------------|------------------------------------------------------------|
| **Accuracy** | Proporsi prediksi yang benar terhadap seluruh data. | `Accuracy = (TP + TN) / (TP + TN + FP + FN)` |
| **Precision** | Dari semua prediksi churn, berapa banyak yang benar-benar churn. | `Precision = TP / (TP + FP)` |
| **Recall** | Dari semua pelanggan yang churn, berapa banyak yang berhasil diprediksi. | `Recall = TP / (TP + FN)` |
| **F1 Score** | Harmonic mean dari precision dan recall, seimbang untuk data tidak seimbang. | `F1 Score = 2 × (Precision × Recall) / (Precision + Recall)` |
| **ROC-AUC Score** | Mengevaluasi kemampuan model membedakan antara churner dan non-churner secara keseluruhan, selain itu jika data churn imbalanced ROC-AUC lebih stabil dibandingkan akurasi. | `AUC = ∫ TPR d(FPR)` dimana TPR = Recall dan FPR = FP/(FP+TN) |

## Keterangan:
- **TP (True Positive)**: Prediksi churn yang benar (actual churn, predicted churn)
- **TN (True Negative)**: Prediksi tidak churn yang benar (actual tidak churn, predicted tidak churn)
- **FP (False Positive)**: Prediksi churn yang salah (actual tidak churn, predicted churn)
- **FN (False Negative)**: Prediksi tidak churn yang salah (actual churn, predicted tidak churn)

## Confusion Matrix:
```
                 Predicted
               Tidak Churn  Churn
Actual Tidak      TN        FP
       Churn      FN        TP
```

---

### 2. Hasil Evaluasi Model

| Model               | Accuracy | Precision (Churn) | Recall (Churn) | F1-Score (Churn) | ROC-AUC |
|---------------------|----------|-------------------|----------------|------------------|------------------|
| **Random Forest**        | 0.91     | 0.67              | 0.72           | 0.69             | 0.8825             |
| **Tuned Random Forest**  | 0.91     | 0.68              | 0.74           | 0.71             | 0.8843            |
| **XGBoost**        | 0.91     | 0.68              | 0.71           | 0.69             | 0.8697            |
| **Tuned XGBoost**  | 0.91     | 0.70              | 0.70           | 0.70             | 0.8655             |

---

### 3. Analisis Hasil
- Random Forest, Tuned XGBoost, dan XGBoost menunjukkan performa yang cukup baik, dengan metrik yang lebih seimbang.
- **Model terbaik adalah Tuned Random Forest**, karena:
  - Berdasarkan ROC-AUC Score (0.854) yang paling tinggi dan stabilitas metrik lainnya, Tuned Random Forest menjadi model terbaik secara keseluruhan. AUC ini menunjukkan bahwa Random Forest lebih baik membedakan churner vs non-churner pada semua threshold.

---

### 📝 Evaluasi terhadap Business Understanding
Model **Tuned Random Forest** dipilih sebagai model final karena memberikan trade-off terbaik antara akurasi keseluruhan dan kemampuan mendeteksi pelanggan yang berisiko churn. Model ini cocok digunakan dalam strategi retention pelanggan berbasis data untuk perusahaan telekomunikasi.

✅ Problem Statements

Bagaimana mengidentifikasi pelanggan yang berpotensi churn?
Model Random Forest (terutama versi Tuned Random Forest) mampu memberikan prediksi churn yang akurat (90%), dengan ROC-AUC Score 0.854 yang tinggi. Ini berarti model bisa membedakan antara pelanggan churner dan non-churner dengan baik, membantu perusahaan mendeteksi risiko churn sejak dini.

Faktor apa saja yang paling berkontribusi?
Model Random Forest (dan XGBoost) memiliki fitur “feature importance” bawaan. Ini akan membantu mengidentifikasi fitur apa yang paling memengaruhi churn (misalnya, durasi layanan, biaya, interaksi dengan layanan pelanggan). Sehingga, perusahaan dapat memprioritaskan upaya retensi secara lebih efektif.

✅ Goals

Membangun model prediksi churn
- ✔️ Sudah tercapai: Model Tuned Random Forest terbukti menjadi model final dengan performa yang memuaskan pada semua metrik evaluasi (accuracy, recall, precision, F1-score, ROC-AUC).
- ✔️ Model ini siap digunakan untuk memprediksi churn pada data pelanggan yang baru.

Mengidentifikasi faktor-faktor utama yang mempengaruhi churn
- ✔️ Sudah tercapai: Feature importance dari Random Forest / XGBoost bisa langsung digunakan untuk analisis bisnis (misalnya, variabel “CustServCalls”, “DayMins”, “ContractRenewal”).

✅ Solution Statements

Membangun dan membandingkan beberapa model
- ✔️ Sudah dilakukan: Empat model diuji: Random Forest, Tuned Random Forest, XGBoost, dan Tuned XGBoost.
- ✔️ Semua metrik diperbandingkan sehingga dapat dipilih model dengan trade-off terbaik.

Hyperparameter tuning
- ✔️ Sudah dilakukan: Pada Random Forest dan XGBoost, tuning meningkatkan stabilitas metrik (meskipun hanya sedikit). Hal ini menunjukkan bahwa pencarian parameter optimal bermanfaat untuk memaksimalkan performa model.

Feature Selection
- ✔️ Dampak Fitur Penting pada Strategi Retensi

   - 📞 CustServCalls paling berpengaruh:
         Banyaknya kontak pelanggan ke CS bisa menandakan ketidakpuasan atau masalah yang tidak terselesaikan. Insight bisnis: perusahaan perlu proaktif menangani keluhan pelanggan dan meningkatkan kualitas 
         layanan CS.

    - 📈 DayMins dan 💰 MonthlyCharge:
         Penggunaan tinggi dan tagihan besar bisa memicu churn jika pelanggan merasa tidak sebanding. Strategi: sediakan program loyalitas atau diskon bagi pelanggan dengan pemakaian tinggi.
