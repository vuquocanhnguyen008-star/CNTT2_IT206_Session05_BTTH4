# Bài thực hành 4: Phân tích kết quả học tập và đề xuất giải pháp cải thiện

## 1. Hiểu đề

Có điểm 5 sinh viên trong 3 tuần. Cần prompt dùng CoT để: tính tăng giảm điểm, tìm sinh viên sa sút, so sánh, nêu điều cần giáo viên xác minh, đề xuất giải pháp. Chỉ dùng dữ liệu cho sẵn, **không đoán nguyên nhân**.

| Sinh viên | Tuần 1 | Tuần 2 | Tuần 3 |
| --- | --- | --- | --- |
| An | 8 | 7 | 5 |
| Bình | 7 | 6 | 4 |
| Chi | 9 | 8 | 8 |
| Dũng | 6 | 5 | 3 |
| Hà | 8 | 8 | 7 |

## 2. Prompt hoàn chỉnh

```
Bạn là trợ lý phân tích học tập, làm việc chính xác và chỉ dựa trên dữ liệu được cung cấp.

Dữ liệu điểm kiểm tra 3 tuần của 5 sinh viên:
An: 8, 7, 5 | Bình: 7, 6, 4 | Chi: 9, 8, 8 | Dũng: 6, 5, 3 | Hà: 8, 8, 7
(Thứ tự là Tuần 1, Tuần 2, Tuần 3.)

Hãy suy nghĩ từng bước một và trình bày phép tính, theo đúng thứ tự:

Bước 1 - Tính toán: với mỗi sinh viên, tính mức thay đổi Tuần 1→2, Tuần 2→3,
         tổng thay đổi Tuần 1→3 (cả số điểm và phần trăm), và điểm trung bình 3 tuần.
         Tính thêm điểm trung bình cả lớp mỗi tuần. Ghi rõ từng phép tính.
Bước 2 - So sánh: so sánh kết quả giữa các sinh viên (xếp hạng điểm Tuần 3,
         so mức giảm giữa các sinh viên).
Bước 3 - Nhận định: xác định sinh viên có dấu hiệu sa sút. Quy ước: sa sút là điểm
         giảm ở cả hai khoảng tuần liên tiếp. Sinh viên giảm một khoảng thì ghi
         "cần theo dõi".
Bước 4 - Đề xuất: đưa giải pháp hỗ trợ học tập phù hợp cho từng nhóm.

Quy tắc bắt buộc:
- Chỉ dùng dữ liệu được cung cấp. Không tự thêm thông tin.
- KHÔNG suy diễn nguyên nhân khiến sinh viên giảm điểm. Nếu cần nói về nguyên nhân,
  hãy ghi vào mục "Điều cần giáo viên xác minh".
- Mọi nhận định phải kèm số liệu chứng minh.

Kết quả gồm: (1) bảng phân tích 5 sinh viên, (2) nhóm sinh viên có dấu hiệu sa sút,
(3) nhận xét so sánh, (4) danh sách vấn đề cần giáo viên xác minh thêm,
(5) đề xuất giải pháp cải thiện.
```

## 3. Kết quả mong đợi (đã tính tay để đối chiếu)

**Bảng phân tích 5 sinh viên**

| Sinh viên | T1→T2 | T2→T3 | Tổng T1→T3 | % giảm | Trung bình 3 tuần | Nhận định |
| --- | --- | --- | --- | --- | --- | --- |
| An | −1 | −2 | −3 | 37,5% | 6,67 | Sa sút |
| Bình | −1 | −2 | −3 | 42,9% | 5,67 | Sa sút |
| Chi | −1 | 0 | −1 | 11,1% | 8,33 | Theo dõi |
| Dũng | −1 | −2 | −3 | 50,0% | 4,67 | Sa sút (nặng nhất) |
| Hà | 0 | −1 | −1 | 12,5% | 7,67 | Theo dõi |

Cách tính ví dụ: An: 7−8 = −1; 5−7 = −2; tổng 5−8 = −3; 3/8 = 37,5%; trung bình (8+7+5)/3 = 6,67.

**Trung bình cả lớp:** Tuần 1: 38/5 = 7,6; Tuần 2: 34/5 = 6,8; Tuần 3: 27/5 = 5,4 (giảm 2,2 điểm). Cả 5 sinh viên đều không tăng điểm.

**So sánh:** Tuần 3 xếp hạng: Chi 8, Hà 7, An 5, Bình 4, Dũng 3. An, Bình, Dũng cùng giảm 3 điểm nhưng Dũng giảm tỷ lệ cao nhất (50%) và có điểm thấp nhất.

**Nhóm có dấu hiệu sa sút:** An, Bình, Dũng (giảm liên tiếp cả hai khoảng tuần, mức giảm tăng lên ở tuần 3). Chi và Hà chỉ giảm nhẹ nên chỉ cần theo dõi.

**Điều cần giáo viên xác minh (không tự đoán):**
- Thang điểm của bài kiểm tra là bao nhiêu?
- Nội dung và độ khó của 3 bài kiểm tra có tương đương nhau không?
- Sinh viên có vắng mặt hoặc nộp thiếu bài trong các tuần đó không?
- Điểm toàn lớp giảm đều (7,6 → 5,4) có do đề kiểm tra khó hơn không?

**Đề xuất giải pháp:**
- Nhóm sa sút (An, Bình, Dũng): giáo viên trao đổi trực tiếp, xác định phần kiến thức còn yếu, ôn tập hoặc phụ đạo ngắn.
- Nhóm theo dõi (Chi, Hà): theo dõi thêm bài kiểm tra tuần sau.
- Cả lớp: rà soát lại độ khó đề và nội dung giảng khi điểm trung bình giảm đều.

## 4. Kết quả chạy thử

*(Bạn tự chạy prompt trên AI, dán bảng phân tích và nhận xét vào đây, đối chiếu với mục 3.)*

Mô hình dùng: *(điền)*

| Tiêu chí kiểm tra | Kết quả thật |
| --- | --- |
| Các phép tính có khớp mục 3 không? | *(điền)* |
| AI có tự đoán nguyên nhân sinh viên giảm điểm không? | *(điền)* |
| Nhận định nào cũng có số liệu chứng minh? | *(điền)* |
| Có mục "cần giáo viên xác minh"? | *(điền)* |

## 5. Nhận xét

- CoT chia bài thành tính toán, so sánh, nhận định, đề xuất nên dễ kiểm tra số liệu.
- Ràng buộc "không suy diễn nguyên nhân" giúp AI chỉ nêu vấn đề cần xác minh chứ không kết luận bừa.
