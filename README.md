# CNTT2.
Dưới đây là lời giải chi tiết và hướng dẫn các bước thực hiện cho **Bài 1: Chuẩn hóa quy trình đối soát giao dịch ví điện tử** thuộc phần Bài tập về nhà (BTVN) Buổi 12 môn Nhập Môn Công Nghệ Thông Tin trên hệ thống LMS:

---

1. **Phần 1: Phân tích (Xác định Record và Field trong bảng Excel giao dịch):**
* **Khái niệm Field (Trường dữ liệu / Cột):** Là các thuộc tính định danh cho từng thông tin cấu thành nên một bản ghi, ví dụ trong bảng đối soát gồm: *Mã giao dịch (Transaction_ID)*, *Ngân hàng đối tác*, *Số tiền*, *Thời gian*, và *Trạng thái giao dịch*.
* **Khái niệm Record (Bản ghi / Dòng):** Là một tập hợp toàn bộ các thông tin chi tiết gắn liền với một giao dịch cụ thể duy nhất (mỗi dòng dữ liệu tương ứng với một bản ghi giao dịch hoàn chỉnh).
* **Tác dụng chuẩn hóa:** Việc phân định rõ ràng các Field và Record giúp hệ thống dữ liệu tuân thủ chuẩn Database, tránh lỗi trùng lặp và làm tiền đề quan trọng để sử dụng các hàm tra cứu như `VLOOKUP`.


2. **Phần 2: Triển khai (Bộ 3 file Word, Excel, PowerPoint):**
* **Chức năng 1 (Word - SRS):** Thiết kế cấu trúc tài liệu mô tả tính năng hoàn tiền dài 5 trang. Bắt buộc sử dụng Auto TOC (Mục lục tự động) thông qua hệ thống phân cấp Heading 1 và Heading 2 rõ ràng.
* **Chức năng 2 (Excel - Đối soát phí):**
* Dùng hàm `TRIM` để làm sạch dữ liệu, loại bỏ khoảng trắng thừa.
* Sử dụng hàm `VLOOKUP` (với tham số `FALSE` / `0` để tìm kiếm chính xác tuyệt đối) nhằm tra cứu tên người dùng từ mã giao dịch.
* *Lưu ý ràng buộc:* Tuyệt đối không được Merge Cell trong vùng dữ liệu và không để hàng trống giữa các bản ghi.


* **Chức năng 3 (PowerPoint - Báo cáo lỗ lãi):** Thiết kế slide doanh thu tháng 05/2024 theo Rule 10/20/30, trong đó tiêu đề phải là *Assertion Title* (ví dụ: *"Doanh thu tăng 15% nhờ ưu đãi nạp điện thoại"*), font chữ tối thiểu 30pt và sử dụng biểu đồ trực quan thay vì bảng số liệu thô.


3. **Phần 3: Kiểm thử và Xử lý lỗi #N/A trong VLOOKUP:**
Khi bảng tra cứu trả về lỗi `#N/A`, hãy thực hiện quy trình 4 điểm sau để tìm nguyên nhân:

1. **Kiểm tra khoảng trắng thừa:** Dữ liệu có chứa dấu cách ẩn đầu hoặc cuối chuỗi hay không (khắc phục bằng hàm `TRIM`).
2. **Kiểm tra định dạng dữ liệu (Data Type):** Đảm bảo mã giao dịch ở bảng chính và bảng tra cứu đều ở cùng một định dạng (đều là Text hoặc đều là Number). Lỗi thường gặp là một bên là số còn bên kia là dạng Text.
3. **Kiểm tra vùng tham chiếu (Table_array):** Xác định xem vùng chọn trong `VLOOKUP` đã được cố định tuyệt đối bằng ký hiệu `$` chưa (ví dụ: `\$A\$2:\$E\$100`), tránh bị lệch vùng khi kéo công thức.
4. **Kiểm tra chỉ số cột (Col_index_num):** Xác định số thứ tự cột cần lấy dữ liệu đã chính xác so với bảng tra cứu chưa (cột đầu tiên trong vùng chọn là 1).
