# 📚 BIG DATA: Spam Email Classification Using PySpark

## 🧩 Pengertian Proyek
Proyek ini bertujuan untuk membangun sistem **klasifikasi email spam** menggunakan **algoritma machine learning berbasis PySpark**. Dengan memanfaatkan kekuatan *distributed computing* dari Spark, proyek ini dapat mengolah dataset besar secara efisien untuk membedakan antara email yang **sah (ham)** dan **tidak diinginkan (spam)**.

---

## 🧾 Deskripsi Proyek
Klasifikasi email spam merupakan salah satu aplikasi penting dalam *Natural Language Processing (NLP)* dan keamanan siber. Proyek ini memanfaatkan kombinasi **2007 TREC Public Spam Corpus** dan **Enron-Spam Dataset**, yang berisi lebih dari **83.000 email**.

Tahapan meliputi:
- Eksplorasi dan pembersihan data.
- Pra-pemrosesan teks dengan teknik NLP.
- Ekstraksi fitur menggunakan **TF-IDF**.
- Pelatihan model klasifikasi menggunakan **Logistic Regression**, **Random Forest**, dan **Gradient Boosted Trees**.
- Evaluasi model menggunakan metrik **accuracy**, **precision**, **recall**, **F1-score**, serta **RMSE** dan **MAE**.

---

## 📂 Dataset

### **Sumber Data**
Dataset ini merupakan gabungan dari dua sumber utama:
1. **TREC 2007 Public Spam Corpus**  
   [🔗 Tautan Asli](https://plg.uwaterloo.ca/~gvcormac/treccorpus07/)
2. **Enron Spam Dataset**  
   [🔗 Tautan Asli](https://www2.aueb.gr/users/ion/data/enron-spam/)

### **Deskripsi Dataset**
Dataset terdiri dari **83.446 data email** dengan dua kolom utama:
- `label`:  
  `1` → spam  
  `0` → ham (non-spam)
- `text`:  
  Isi pesan email dalam bentuk teks mentah.

### **Tujuan Klasifikasi**
- Menyaring email spam sebelum mencapai kotak masuk pengguna.
- Meningkatkan efisiensi dan keamanan komunikasi digital.
- Mengurangi paparan terhadap *phishing*, *malware*, dan konten berbahaya.
- Membantu sistem keamanan email otomatis dalam mendeteksi ancaman.

---

## ⚙️ Tools dan Teknologi
Proyek ini menggunakan ekosistem **Big Data** berbasis PySpark dan beberapa pustaka pendukung:

| Tools/Library | Kegunaan |
|----------------|-----------|
| **PySpark** | Pemrosesan dan pelatihan model pada skala besar |
| **Pandas & NumPy** | Manipulasi dan analisis data |
| **Matplotlib & Seaborn** | Visualisasi data |
| **WordCloud** | Analisis kata dominan pada email |
| **Scikit-learn** | Evaluasi performa model (confusion matrix, classification report) |
| **TF-IDF (Term Frequency – Inverse Document Frequency)** | Ekstraksi fitur teks |
| **Google Colab / Kaggle** | Lingkungan eksekusi berbasis cloud |

---

## 🔍 Tahapan Analisis

### 1️⃣ Exploratory Data Analysis (EDA)
- Mengevaluasi jumlah data spam dan ham.
- Menganalisis panjang email rata-rata per kategori.
- Visualisasi distribusi email spam vs ham menggunakan **bar chart**.
- Membuat **word cloud** untuk melihat kata dominan di setiap kelas.

### 2️⃣ Data Preprocessing
Langkah-langkah utama dalam pemrosesan teks:
- **StringIndexer**: Konversi label `spam/ham` menjadi nilai numerik.  
- **Tokenizer**: Memecah teks menjadi kata-kata individual.  
- **StopWordsRemover**: Menghapus kata umum yang tidak bermakna.  
- **HashingTF**: Mengubah kata menjadi representasi numerik berdasarkan frekuensi.  
- **IDF (Inverse Document Frequency)**: Memberi bobot lebih pada kata-kata yang jarang muncul untuk meningkatkan akurasi model.

### 3️⃣ Split Dataset
Dataset dibagi menjadi:
- **Training set:** 80%  
- **Testing set:** 20%

Visualisasi *pie chart* digunakan untuk memastikan distribusi kelas seimbang.

### 4️⃣ Model Training
Tiga model diuji menggunakan **Spark MLlib**:

| Model | Accuracy | Karakteristik |
|--------|-----------|----------------|
| Logistic Regression | 🟢 **0.97** | Performa tertinggi, linear dan stabil |
| Random Forest | 🟡 **0.81** | Akurasi lebih rendah, cenderung overfit |
| Gradient Boosted Trees | 🟠 **0.90** | Menangani non-linearitas, namun masih di bawah Logistic Regression |

### 5️⃣ Evaluasi Model
Evaluasi dilakukan menggunakan:
- **Confusion Matrix**  
- **Classification Report**  
- **Accuracy**, **Precision**, **Recall**, **F1-score**  
- **RMSE** dan **MAE** untuk mengukur kesalahan rata-rata prediksi

Visualisasi heatmap digunakan untuk membandingkan prediksi benar dan salah antar kelas.

---

## 📊 Hasil Akhir Analisis
Hasil evaluasi menunjukkan:

| Model | Accuracy | Precision | Recall | F1-score |
|--------|-----------|------------|---------|-----------|
| **Logistic Regression** | **0.97** | 0.96 | 0.97 | 0.96 |
| **Gradient Boosted Trees** | 0.90 | 0.96 | 0.82 | 0.88 |
| **Random Forest** | 0.81 | 0.95 | 0.61 | 0.74 |

Model terbaik adalah **Logistic Regression**, dengan performa konsisten pada kedua kelas “Ham” dan “Spam”.

---

## 💡 Insight dan Manfaat

### 🔎 Insight
- **Logistic Regression** unggul karena data cenderung memiliki pola linear.  
- **TF-IDF** berhasil menangkap konteks kata yang relevan untuk membedakan spam dari ham.  
- **Random Forest** dan **GBT** menunjukkan kemampuan dalam mengenali pola non-linear, namun performanya menurun akibat ketidakseimbangan data.

### 🚀 Manfaat
- Dapat diterapkan dalam sistem penyaringan email real-time.  
- Membantu meningkatkan keamanan siber dengan mendeteksi ancaman berbasis teks.  
- Menjadi dasar untuk pengembangan model NLP lain seperti *phishing detection* atau *sentiment analysis*.  
- Dapat diadaptasi ke platform Big Data dengan volume data besar (mis. Gmail, Outlook filter engine).

---

## 🧭 Kesimpulan Akhir
Proyek **Spam Email Classification Using PySpark** berhasil membangun pipeline lengkap untuk klasifikasi teks dalam skala besar.  
Dengan akurasi hingga **97%**, model **Logistic Regression dengan TF-IDF** terbukti paling efektif dalam mendeteksi email spam.  
Implementasi berbasis **PySpark** membuat sistem ini dapat diskalakan untuk pemrosesan data masif, menjadikannya solusi efisien dan andal untuk industri keamanan email modern.

---

## 👩‍💻 Tim Pengembang
| Nama | NRP |
|------|------|
| **Mutiara Nurhaliza** | 5027221010 |
| **Rehana Putri Salsabilla** | 5027221015 |
| **Salsabila Amalia Harjanto** | 5027221023 |

---
