# 🏆 DATATHON 2026 — E-Commerce Strategic Intelligence & Predictive Analytics Platform

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg?logo=python)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebooks-orange.svg?logo=jupyter)](https://jupyter.org/)
[![Machine Learning](https://img.shields.io/badge/Models-Revenue%20Forecasting-green.svg)](https://scikit-learn.org/)
[![Visualization](https://img.shields.io/badge/Visualization-Plotly%20%7C%20Seaborn%20%7C%20Matplotlib-ff4b4b.svg)](https://matplotlib.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success.svg)](#)

---

## 📌 Executive Summary

Dự án phát triển giải pháp phân tích kinh doanh và mô hình dự báo toàn diện cho bài toán tối ưu hóa vận hành của doanh nghiệp Thương mại Điện tử Thời trang (2012–2022+). 

Dựa trên **Khung Phân Tích Đa Phòng Ban (Cross-Departmental KPI Framework)**, bài làm tích hợp giữa **Mô hình Dự báo Doanh thu (Forecast Revenue Model)** và **Hệ thống Trực quan hóa Chuyên sâu (Visualization Suite)** nhằm giải mã các điểm nghẽn hệ thống:
* **Promo Cannibalization Trap:** Khách hàng lệ thuộc khuyến mãi (>80% cannibalization), bào mòn biên lợi nhuận.
* **Deadstock Capital Stagnation:** 95% giá trị tồn kho không phát sinh đơn >90 ngày, đối lập với việc cháy hàng (stockout) Top 5% Hero SKUs vào mùa cao điểm (Tháng 11 & 12).
* **Triple Squeeze Effect:** Chi phí logistics tăng, đứt hàng gây mất doanh thu (lost sales) và tỷ lệ hoàn hàng tăng đồng thời vào dịp cuối năm.

---

## 📂 Cấu Trúc Repository (Project Structure)

Dưới đây là sơ đồ cấu trúc tệp tin thực tế của dự án:

```text
├── Cleaned_data/                              # Bộ dữ liệu đã qua tiền xử lý, làm sạch & feature engineering
├── Forecast Reveue Model/                     # Thư mục chứa code, checkpoints và artifact mô hình dự báo doanh thu
├── Raw_data/                                  # Dữ liệu thô ban đầu do BTC Datathon cung cấp
├── Styles/                                    # Assets, cấu hình CSS/Formatting cho visuals & notebooks
│   └── Styles/                                
├── 1_Questions.ipynb                          # Notebook xử lý bài toán, trả lời câu hỏi nghiệp vụ & EDA
├── Visualization.ipynb                        # Notebook trực quan hóa toàn bộ biểu đồ 6 phòng ban & insights
├── [DATATHON26'] KPI Framework by ...pdf      # Tài liệu tổng hợp KPI Framework, chẩn đoán hệ thống & đề xuất
└── README.md                                  # Tài liệu hướng dẫn & tổng quan dự án
```

---

## 🏛️ Khung Phân Tích 6 Phòng Ban (KPI Framework Architecture)

Dự án bám sát khung KPI chuẩn hóa để đánh giá toàn diện sức khỏe doanh nghiệp:

| Phòng ban | KPI / Chỉ số trọng yếu | Hiện trạng & Insights chẩn đoán |
| :--- | :--- | :--- |
| **D1. Commercial & Revenue** | Promo Penetration, Cannibalization Rate, Hero SKU Share | Penetration ~39%, Cannibalization >80%. Top 5% SKU gánh >60% doanh thu. |
| **D2. Customer Intelligence** | Repurchase Cohorts, Inter-order Gap, Churn Threshold | Gap median 144 ngày, Churn threshold 288 ngày. Cohort 2018–2022 giảm sâu retention do thói quen săn sale. |
| **D3. Inventory & Supply Chain** | Sell-through Rate (STR), Deadstock Ratio | Deadstock chiếm 95% vốn đọng (>90 ngày không phát sinh đơn); STR đa số SKU <12%. |
| **D4. Logistics & Reverse Ops** | Return Rate, Shipping Lead Time, Payment Mix | Return <20% (chủ yếu do "wrong size" Streetwear); COD có tỷ lệ hủy đơn cao nhất. |
| **D5. Marketing Performance** | Email Campaign ROI, Organic Search Share, Paid Mix | Email là kênh owned có chất lượng cao nhất (Bounce 0.0045, Duration 3.54p) nhưng thiếu đầu tư. |
| **D6. UX & Conversion** | Return Visit Rate, Bounce Rate, Session Duration | Sessions/Unique Visitors > 1 (khách có xu hướng so sánh giá nhiều hơn trước khi chốt đơn). |

---

## 🤖 Mô Hình Dự Báo Doanh Thu (Forecast Revenue Model)

Nằm trong thư mục `Forecast Reveue Model/`, mô hình được xây dựng để dự phóng doanh thu theo chu kỳ và giảm thiểu rủi ro đứt gãy chuỗi cung ứng:
* **Mục tiêu:** Dự báo nhu cầu thị trường và doanh thu theo mùa vụ (đặc biệt là giai đoạn Q4 Peak: Tháng 11 & 12).
* **Đặc trưng đầu vào (Features):** Chuỗi thời gian doanh thu lịch sử, hệ số mùa vụ, biến động khuyến mãi (Promo Depth), tỷ lệ thâm nhập đơn hàng và hành vi phân nhóm khách hàng.
* **Đầu ra:** Dự báo doanh thu chi tiết theo từng danh mục, hỗ trợ kế hoạch nhập hàng cho Hero SKUs và giảm thiểu chi phí cơ hội do Stockout.

---

## 📊 Trực Quan Hóa Dữ Liệu (`Visualization.ipynb` & `1_Questions.ipynb`)

Notebooks phân tích và trực quan hóa chuyên sâu giải quyết các bài toán trọng tâm:

1. **Cohort Repurchase Retention Matrix:** Minh họa sự sụt giảm tỷ lệ giữ chân khách hàng từ >50% (cohort 2012–2013) xuống <10% (cohort 2018–2019).
2. **STR vs Stockout Frequency Quadrant:** Phân loại toàn bộ danh mục sản phẩm thành: *Hero SKUs, Core/Cash Cows, Deadstock Candidates*.
3. **Triple Squeeze Seasonal Diagnostic:** Tích hợp đa trục biểu đồ thể hiện sự suy giảm biên lợi nhuận vào Tháng 11 & 12 (Shipping Cost tăng, Lost Revenue do Stockout, Return Rate tăng).
4. **Channel Quality Matrix:** So sánh Bounce Rate, Session Duration và Return Visit Rate giữa các nguồn Organic, Paid và Email.

---

## 🎯 Đề Xuất Chiến Lược Hành Động (Actionable Recommendations)

1. **Phá vỡ vòng xoáy Promo:** Thiết kế lại Loyalty Program dựa trên giá trị (Early access, Private drops, Free shipping có điều kiện) thay vì đua giảm giá trực tiếp.
2. **Giải phóng vốn chết:** Tái phân bổ tồn kho từ deadstock candidates sang tăng chiều sâu (depth) cho Top 5% Hero SKUs trước mùa cao điểm Q4.
3. **Phát triển Owned Audience:** Chuyển dịch ngân sách sang xây dựng Email list và tối ưu hóa Organic Search để giảm thiểu chi phí quảng cáo và phí hoa hồng sàn TMĐT.

---

## 🚀 Hướng Dẫn Sử Dụng & Khởi Chạy

### 1. Chuẩn bị môi trường
```bash
# Clone repository
git clone https://github.com/alobipbop/last-dance.git
cd last-dance

# Tạo và kích hoạt môi trường ảo
python -m venv venv
# Trên Linux/macOS:
source venv/bin/activate
# Trên Windows:
venv\Scripts\activate

# Cài đặt thư viện phụ thuộc
pip install pandas numpy scikit-learn matplotlib seaborn plotly jupyter
```

### 2. Khởi chạy Notebooks
```bash
jupyter notebook
```
* Mở **`1_Questions.ipynb`** để theo dõi toàn bộ quy trình tiền xử lý, khám phá dữ liệu và giải quyết các câu hỏi phân tích.
* Mở **`Visualization.ipynb`** để xem hệ thống dashboard và visual insights.
* Truy cập **`Forecast Reveue Model/`** để kiểm tra và huấn luyện mô hình dự báo doanh thu.

---

## 👥 Tác Giả & Cuộc Thi
* **Repository:** `alobipbop/datathon2026-ecommerce-analytics`
* **Đơn vị:** Tennhom - National Economics University (NEU)
* **Cuộc thi:** Datathon 2026
