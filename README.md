# quan-ly-nhap-ban

## Xuất ZIP để kiểm tra định kỳ

Mở ứng dụng trên đúng thiết bị/trình duyệt đã lưu dữ liệu rồi truy cập **[trang xuất ZIP](./export.html)**. Chọn ngày bắt đầu/kết thúc (đều tính vào phạm vi), rồi nhấn **Tạo và tải ZIP**. Trang xuất độc lập này đọc `SimpleTradeDB/records` và đối chiếu với bản dự phòng `simpleTradeRecords` trong localStorage. Nếu cả hai nguồn cùng có ID nhưng khác nội dung, ZIP giữ cả biến thể và hiện cảnh báo; bản ghi chỉ có ở một nguồn cũng được giữ. Không ghi lại/xóa dữ liệu ứng dụng.

Gói gồm `transactions.json`, `transactions.csv` (UTF-8 BOM cho Excel), `manifest.json`, `evidence-index.csv/json`, `CHATGPT-GUIDE.md`, danh sách chữ ký mẫu và thư mục `evidence/` chứa ảnh thực tế đã giải mã từ data URL (hóa đơn, chuyển khoản và chữ ký). Schema ngày: nhập hàng/phiếu chi dùng trường ngày `YYYY-MM-DD`; bán hàng dùng timestamp ISO và được lọc theo ngày địa phương của thiết bị. ZIP không nén để giảm tải CPU; có ngưỡng đầu vào 20 MiB cho iPhone/iPad và 100 MiB cho thiết bị khác, cùng giới hạn ZIP32.

Nút kiểm thử trên trang xuất dùng dữ liệu giả trong bộ nhớ, không ghi vào kho thật. Kiểm tra CRC/cấu trúc trong trình duyệt là kiểm tra nội bộ, không phải giải nén bằng công cụ độc lập. Nếu cần kiểm định triển khai, hãy giải nén tệp ZIP tải xuống bằng Finder/Files/7-Zip và mở JSON/CSV/ảnh. Ứng dụng nguồn nén ảnh trước khi lưu, vì vậy ảnh trong ZIP là bản đang lưu; ảnh gốc trước nén không thể khôi phục. Chứng từ/chữ ký có thể nhạy cảm; chỉ chia sẻ với người được phép.
