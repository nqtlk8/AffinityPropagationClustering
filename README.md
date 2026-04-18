# Phân cụm Khách hàng sử dụng Thẻ Tín dụng (Credit Card Customer Segmentation)

Dự án này tập trung vào việc phân nhóm khách hàng dựa trên hành vi sử dụng thẻ tín dụng trong vòng 6 tháng. Mục tiêu cốt lõi là giúp ngân hàng/tổ chức tài chính hiểu rõ các đặc điểm khác nhau của từng nhóm khách hàng, từ đó xây dựng các chiến lược Marketing cá nhân hóa hiệu quả.

## 1. Bài toán (Problem Statement)
Việc xác định chiến lược tiếp thị phù hợp cho từng phân khúc khách hàng là yếu tố then chốt để tối ưu doanh thu và trải nghiệm người dùng. Dự án sử dụng các kỹ thuật học máy không giám sát (Unsupervised Learning) để tự động phân nhóm khoảng 1000 chủ thẻ tín dụng đang hoạt động dựa trên 4 biến hành vi.

## 2. Dữ liệu (Dataset)
Bộ dữ liệu tóm tắt hành vi sử dụng của khoảng 9000 khách hàng với các thông tin chi tiết như sau:

| Tên biến | Mô tả |
| :--- | :--- |
| **CUST_ID** | Mã định danh khách hàng. |
| **BALANCE** | Số dư còn lại trong tài khoản để thực hiện mua sắm. |
| **BALANCE_FREQUENCY** | Tần suất cập nhật số dư (0 đến 1). |
| **PURCHASES** | Tổng số tiền mua sắm thực hiện từ tài khoản. |
| **ONEOFF_PURCHASES** | Số tiền mua sắm tối đa thực hiện trong một lần thanh toán. |
| **INSTALLMENTS_PURCHASES** | Số tiền mua sắm thực hiện theo hình thức trả góp. |
| **CASH_ADVANCE** | Tiền mặt được người dùng rút trước. |
| **PURCHASES_FREQUENCY** | Tần suất thực hiện mua sắm (0 đến 1). |
| **ONEOFF_PURCHASES_FREQ** | Tần suất mua sắm một lần (One-go). |
| **PURCHASES_INSTALLMENTS_FREQ** | Tần suất mua sắm trả góp. |
| **CASH_ADVANCE_FREQUENCY** | Tần suất trả tiền mặt rút trước. |
| **CASH_ADVANCE_TRX** | Số lượng giao dịch "Rút tiền mặt trước". |
| **PURCHASES_TRX** | Số lượng giao dịch mua sắm đã thực hiện. |
| **CREDIT_LIMIT** | Hạn mức thẻ tín dụng của người dùng. |
| **PAYMENTS** | Tổng số tiền đã thanh toán. |
| **MINIMUM_PAYMENTS** | Số tiền thanh toán tối thiểu đã thực hiện. |
| **PRCFULL_PAYMENT** | Tỷ lệ phần trăm trên tổng số tiền đã thanh toán đầy đủ. |
| **TENURE** | Thời hạn sử dụng dịch vụ thẻ tín dụng của người dùng. |

Trong các biến trên, mình chọn 4 biến gồm: BALANCE, BALANCE_FREQUENCY, PURCHASES và CREDIT_LIMIT làm các biến chính để phân nhóm

## 3. Phương pháp thực hiện & Thuật toán
Dự án áp dụng quy trình phân tích dữ liệu chuẩn bao gồm: tiền xử lý và thực hiện phân cụm.

### Thuật toán sử dụng:
* **K-Means Clustering:** Thuật toán phân cụm dựa trên khoảng cách, hiệu quả với tập dữ liệu lớn.
* **Affinity Propagation:** Thuật toán phân cụm không yêu cầu xác định trước số lượng cụm, giúp tìm ra các cấu trúc tiềm ẩn tự nhiên trong dữ liệu.

### Phương pháp tối ưu hóa số cụm:
Để tìm ra số lượng nhóm khách hàng tối ưu nhất, chúng tôi sử dụng:
* **Elbow Method (Phương pháp khuỷu tay):** Quan sát độ biến thiên (Inertia) để tìm điểm gãy.
* **Silhouette Score:** Đánh giá độ tách biệt và sự gắn kết của các cụm để đảm bảo chất lượng phân loại.

## 4. Công nghệ sử dụng
* **Ngôn ngữ:** Python
* **Thư viện:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn.
* **Môi trường:** Jupyter Notebook
## 5. Kết quả mong đợi
Dự án hướng tới việc xác định các phân khúc khách hàng chính như:
* **Khách hàng chi tiêu cao (Big Spenders):** Nhóm mua sắm nhiều, hạn mức tín dụng cao.
* **Khách hàng rút tiền mặt (Cash Advance Users):** Nhóm thường xuyên rút tiền mặt thay vì mua sắm trực tiếp.
* **Khách hàng kỷ luật (Prudent Users):** Nhóm có số dư thấp và luôn thanh toán đầy đủ đúng hạn.
* **Khách hàng trả góp (Installment Users):** Nhóm ưa chuộng các hình thức mua sắm chia nhỏ kỳ hạn.

---
