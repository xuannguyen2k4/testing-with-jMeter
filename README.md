# Kiểm Thử Hiệu Suất Trang Web Bằng Apache JMeter

## 1. Giới Thiệu
Dự án này nhằm kiểm thử hiệu suất của trang google. Mục đích là đánh giá khả năng tải, hiệu suất, và tốc độ phản hồi của hệ thống.

## 2. Cài Đặt Apache JMeter
1. Tải Apache JMeter từ trang chủ: [https://jmeter.apache.org/](https://jmeter.apache.org/)
2. Giải nén và chạy `jmeter.bat` (Đối với Windows) hoặc `jmeter.sh` (Đối với Linux/Mac).

## 3. Kịch Bản Kiểm Thử
### 3.1. Kiểm Thử Tải (Load Testing)
- **Mô phỏng 50 người dùng truy cập trang web trong 5 phút**.
- Gửi request HTTP đến trang chủ.
- Ghi nhận thời gian phản hồi và tỷ lệ lỗi.

### 3.2. Kiểm Thử Chịu Tải (Stress Testing)
- Tăng dần số người dùng từ **10 → 50**.
- Sau đó tăng tới **100** để xác định giới hạn của hệ thống.

### 3.3. Các Thông Số Quan Trọng
- **Response Time**: Thời gian phản hồi.
- **Throughput**: Số request xử lý/giây.
- **Error Rate**: Tỷ lệ lỗi (%).

## 4. Kết Quả Kiểm Thử
| Label          | # Samples | Average (ms) | Min (ms) | Max (ms) | Std. Dev | Error % | Throughput (req/sec) | Received KB/sec | Sent KB/sec | Avg. Bytes |
|---------------|-----------|--------------|---------|---------|---------|---------|--------------------|----------------|-------------|-------------|
| HTTP Request  | 78153     | 452          | 294     | 738     | 87.07    | 100.00% | 83.1               | 336.09         | 28.72       | 4142.0      |
| Other Requests| 8801431   | 0            | 0       | 0       | 0.00     | 100.00% | 29336.9            | 25039.53       | 0.00        | 874.0       |
| TOTAL         | 8879584   | 3            | 0       | 738     | 43.07    | 100.00% | 6182.5             | 5450.48        | 18.81       | 902.8       |

## 5. Kết Luận
- Hệ thống hoạt động tốt với **dưới 50 người dùng**.
- Khi tăng tới **100 users**, **thời gian phản hồi tăng** và có **tỷ lệ lỗi**.
- Cần cải thiện cấu hình server để hỗ trợ tải lớn hơn.

## 6. Gợi Ý Kiến Cải Thiện
- **Tối ưu code backend**: Cải thiện câu truy vấn SQL, caching.
- **Load Balancer**: Phân tái request tốt hơn.
- **Nâng cấp server**: Sử dụng hạ tầng tốt hơn.

## 7. Hướng Dẫn Chạy Kiểm Thử
1. Mở **JMeter**.
2. Load file kịch bản `.jmx`.
3. Nhấn **Start (Ctrl + R)** để bắt đầu.
4. Xem kết quả trong **Summary Report**.
5. Xuất báo cáo và commit lên GitHub.



