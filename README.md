# Bài 3 — GitHub Environments cho Staging và Production

**Sinh viên:** Nguyễn Đăng Dương  
**Lớp:** CNTT2  
**Môn học:** IT209 — Session 12

Workflow `.github/workflows/cd-multi-env.yml` chạy kiểm thử và đóng gói ứng dụng trước khi tạo job triển khai theo nhánh. Push lên `develop` chạy job gắn với environment `staging`; push lên `main` chạy job gắn với environment `production` và sẽ chờ reviewer nếu protection rule của environment được bật.

## Cấu hình Environment

Repository cần có hai environment `staging` và `production`. Trong **Settings → Environments → production**, thêm tài khoản cá nhân của chủ repository vào **Required reviewers**. Workflow sẽ tạo deployment production khi push lên `main`; job chỉ tiếp tục sau khi reviewer duyệt.

Job triển khai tải JAR artifact và ghi nhận lần chạy theo environment. URL hiện là URL mẫu do đề chưa cung cấp máy chủ triển khai staging/production.

## Chạy cục bộ

```bash
./gradlew test bootJar
```

Sau khi tạo environment và reviewer, push commit lên `develop` để kiểm tra staging. Push lên `main` rồi xem tab **Actions** để thấy production chờ phê duyệt.

