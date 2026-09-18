# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602238

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | export lỗi / chưa qua QC | 32 |
| hard_panoptic | chưa có | 0 / 2 | 30 |
| cp1_holes | chưa có | 0 / 1 | 3 |
| cp2_slice | chưa có | 0 / 1 | 3 |
| cp5_occlusion | chưa có | 0 / 1 | 3 |
| cp3_thin | chưa có | 0 / 1 | 3 |
| cp4_curb | chưa có | 0 / 1 | 3 |
| cp6_coverage | chưa có | 0 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach. Tình trạng hiện tại: `medium_instance.zip` có file nhưng script báo lỗi định dạng ở annotation 3 và 31; chưa export lại từ CVAT.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: chưa xác định rõ trong report; task `medium_instance` hiện đang export lỗi và chưa qua QC lại từ CVAT.
- Class và quy tắc tôi dùng để chọn biên: chưa xác định rõ vì task vẫn đang ở trạng thái export lỗi; khi export lại sẽ ghi lại ảnh, vị trí và quy tắc chọn biên đúng theo phần nhìn thấy và class của object.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: chưa dùng / chưa xác định; đang chờ export lại từ CVAT để kiểm tra từng object.
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình. Hiện tại: chưa ghi rõ vì task Medium chưa được export lại đúng chuẩn.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `medium_instance`; annotation 3 và annotation 31 trong ZIP export lỗi.
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: định dạng export / polygon/RLE không hợp lệ.
- Bằng chứng tôi nhìn thấy: khi chạy `python scripts/inspect_submissions.py --dir submissions`, script báo `annotation 3 thiếu polygon/RLE hợp lệ` và `annotation 31 thiếu polygon/RLE hợp lệ`.
- Quy tắc và hành động sửa: theo hướng dẫn repo, không sửa ZIP bằng tay; cần mở lại task `medium_instance` trong CVAT, kiểm từng object lỗi, Save lại và export đúng định dạng COCO 1.0.
- Sau sửa đã Save và export lại chưa? chưa. Chưa export lại từ CVAT.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): script hiện tại cho `medium_instance: LỖI`; chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| `medium_instance` / annotation 3 | 1) là polygon hợp lệ nhưng export bị lỗi; 2) object đó không có dữ liệu polygon/RLE đầy đủ | script báo `annotation 3 thiếu polygon/RLE hợp lệ`; cần kiểm trong CVAT | Chưa quyết định final; cần export lại từ CVAT và kiểm từng object bị lỗi |
| `medium_instance` / annotation 31 | 1) object có mask nhưng dữ liệu export rời rạc; 2) mask đó sai dạng và phải xóa/chỉnh lại | script báo `annotation 31 thiếu polygon/RLE hợp lệ`; lỗi nằm ở export, không phải chỉ điểm | Chờ kiểm lại trong CVAT và export lại đúng COCO 1.0 |
| task `hard_panoptic` và checkpoints chưa kịp | 1) chưa làm; 2) cần nộp một phần và ghi rõ phần còn thiếu | repo yêu cầu ghi `chưa có` nếu chưa làm; không tạo ZIP rỗng | Ghi rõ phần chưa làm và tiếp tục làm thêm khi có thời gian |
