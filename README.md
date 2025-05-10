# Turkce_Hukuk-LLM-FineTuning-QLORA


---

## 🏛️ Türkçe Hukuk LLM Eğitimi – QLoRA ile Geliştirilmiş Yaklaşım

Bu proje, **2024 Teknofest Yapay Zeka Yarışması birincisi** olan hukuk tabanlı dil modeli projesine katkı sağlayan ve bu çalışmayı daha verimli hale getirmeyi amaçlayan bir devam niteliğindedir. Aynı veri seti ve temel model kullanılarak, **QLoRA (Quantized Low-Rank Adaptation)** tekniğiyle **full fine-tuning'e ek olarak** alternatif bir eğitim yöntemi önerilmektedir.

---

### 🎯 Projenin Amacı

* Teknofest 2024 projesinde kullanılan hukuk verisi ve **T5 Efficient Base Türkçe modeli** ile,
* Daha kaynak verimli, esnek ve kolay erişilebilir bir eğitim süreci tasarlamak,
* QLoRA tekniği sayesinde eğitim sırasında yaşanan donanım limitlerini aşmak.

---

### 🧠 Eğitim Sürecinden Çıkarımlar

* Orijinal projede kullanılan `batch_size=8`, Kaggle GPU ortamında klasik fine-tuning sırasında **"out of memory"** hatasına yol açtı.
* Bu nedenle `batch_size` değeri 2’ye düşürülerek eğitim yapılmak zorunda kalındı, fakat eğitim süresi uzadı ve model performansı sınırlı kaldı.
* QLoRA tekniği ile bu sorun ortadan kaldırıldı ve `batch_size=8` tekrar kullanılabilir hale geldi.
* Bu sayede eğitim çok daha verimli ve kararlı şekilde gerçekleştirildi.

#### 🔄 Denenen QLoRA Yapılandırmaları

1. **İlk Deneme**: `num_train_epochs = 5`
2. **İkinci Deneme**: `num_train_epochs = 10`
3. **Üçüncü Deneme**: `batch_size = 16`, `num_train_epochs = 15`
   ➤ `num_train_epochs` artırılmasının nedeni: **Validation loss** hâlâ düşmeye devam ediyordu.

#### 📊 Önemli Bir Gözlem

Veri setinde **aynı cevaba farklı sorularla ulaşan örneklerin** bulunduğu durumlarda, QLoRA ile eğitilmiş modelin performansı **Teknofest’te kullanılan orijinal modele oldukça yakın sonuçlar** vermektedir.
Bu da, QLoRA’nın genelleme kabiliyetinin özellikle **semantik çeşitliliği olan yapılarda** güçlü olduğunu göstermektedir.

---

### ⚙️ Teknik Detaylar

* **Model**: `Turkish-NLP/t5-efficient-base-turkish`
* **Yöntem**: QLoRA (4-bit quantization + LoRA adaptasyonu)
* **LoRA Ayarları**: `r=64`, `alpha=16`, `dropout=0.05`
* **Kütüphaneler**: `transformers`, `datasets`, `peft`, `bitsandbytes`, `accelerate`

---

### 📁 Dosya Açıklamaları

| Dosya                          | Açıklama                                  |
| ------------------------------ | ----------------------------------------- |
| `hukuk-projesi-qlora.ipynb`    | İlk QLoRA denemesi                        |
| `hukuk-projesi-qlora-v2.ipynb` | Parametre iyileştirmeleri içeren versiyon |
| `hukuk-projesi-qlora-v3.ipynb` | En verimli sonuçları üreten final sürüm   |
| `hukuk_projesi_test.ipynb`     | Tüm modellerin performans karşılaştırması |

---

### 🚀 Katkılar ve Yenilik

* Önceki Teknofest projesiyle aynı veri ve model temel alınmış,
* Eğitim sürecine QLoRA gibi modern PEFT yöntemleri entegre edilmiştir,
* Bu sayede klasik eğitimin önündeki bellek sorunları ortadan kaldırılmış, daha hızlı ve etkili bir eğitim mümkün kılınmıştır,
* QLoRA ile elde edilen sonuçlar, özellikle **soru çeşitliliği içeren senaryolarda** yüksek başarı göstermiştir.

---


### 🔗 Referanslar

1. **Teknofest 2024 Hukuk Modeli GitHub Reposu**: [Teknofest Proje GitHub](https://github.com/xxxxxx)  
2. **Veri Seti - Hugging Face**: [Hukuk Veri Seti Hugging Face](https://huggingface.co/datasets/xxxxxx)  
3. **Geliştirdiğim Modeller**: [Benim Model Reposu](https://github.com/xxxxxx)
---
### 📈 Yapılabilecek İyileştirmeler

* Eğitim sayısı artırılabilir,
* Teknofest modelindeki gibi ROUGE değerlerine bakılabilir,
* Farklı LLM'ler denenebilir.

---
