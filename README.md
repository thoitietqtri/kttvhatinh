
# KTTV Hà Tĩnh — Auto Upload Bản tin

Tự động đăng nhập và **upload file PDF** lên cổng: `http://222.255.11.117:8888/UploadFile.aspx` (Hà Tĩnh).  
Sử dụng **GitHub Actions + Playwright** (không cần máy chủ riêng).

## Cấu trúc
```
.
├─ .github/workflows/upload.yml   # Workflow chạy tự động / thủ công
├─ tools/playwright_uploader.py   # Script Playwright: đăng nhập + upload
├─ bantin/                        # Thư mục chứa file PDF cần up
└─ .gitignore
```

## Thiết lập Secrets (bắt buộc)
Vào **Settings → Secrets and variables → Actions** của repo `kttvhatinh` và tạo 4 secrets:
- `USERNAME` = `HTIN`
- `PASSWORD` = `HTIN`
- `PORTAL_URL` = `http://222.255.11.117:8888/Login.aspx`
- `UPLOAD_URL` = `http://222.255.11.117:8888/UploadFile.aspx`

> Lưu ý: Không commit mật khẩu vào code!

## Đặt file cần up
Đặt file PDF bản tin vào thư mục `bantin/`. Script sẽ chọn **file mới nhất** trong thư mục này.

## Chạy thủ công
Vào tab **Actions → Auto Upload Bản tin (Hà Tĩnh)** → **Run workflow**.

## Lịch chạy tự động
Workflow mặc định đặt cron chạy 04:30 ICT mỗi ngày (tức **21:30 UTC** ngày hôm trước). Có thể chỉnh trong `.github/workflows/upload.yml`.

## Nhật ký & bằng chứng
Sau khi chạy, workflow sẽ đính kèm:
- `after_upload.png` (ảnh chụp màn hình sau khi upload).
- `tools/uploader.log` (log chi tiết).

## Yêu cầu
- GitHub Actions: `ubuntu-latest`.
- Python 3.11+.
- Playwright browsers (workflow đã cài tự động).
