| Chức năng                                             | Method | URL                     | Query params (nếu có)         | Status thành công | Status lỗi (ví dụ) |
| ----------------------------------------------------- | -----: | ----------------------- | ----------------------------- | ----------------- | ------------------ |
| Lấy danh sách sách (có phân trang & lọc theo tác giả) |    GET | `/books`                | `?page=1&limit=10&author=...` | `200 OK`          | `400 Bad Request`  |
| Thêm sách mới                                         |   POST | `/books`                | Không                         | `201 Created`     | `400 Bad Request`  |
| Lấy chi tiết một sách                                 |    GET | `/books/{id}`           | Không                         | `200 OK`          | `404 Not Found`    |
| Cập nhật toàn bộ thông tin sách                       |    PUT | `/books/{id}`           | Không                         | `200 OK`          | `404 Not Found`    |
| Cập nhật số lượng sách (chỉ 1 trường)                 |  PATCH | `/books/{id}`           | Không                         | `200 OK`          | `400 Bad Request`  |
| Xóa sách                                              | DELETE | `/books/{id}`           | Không                         | `204 No Content`  | `404 Not Found`    |
| Lấy danh sách thẻ mượn của một sách (sub-resource)    |    GET | `/books/{bookId}/loans` | `?page=1&limit=10`            | `200 OK`          | `404 Not Found`    |
| Tạo thẻ mượn mới                                      |   POST | `/loans`                | Không                         | `201 Created`     | `400 Bad Request`  |
| Lấy chi tiết một thẻ mượn                             |    GET | `/loans/{id}`           | Không                         | `200 OK`          | `404 Not Found`    |
| Trả sách (cập nhật ngày trả)                          |  PATCH | `/loans/{id}`           | Không                         | `200 OK`          | `404 Not Found`    |


Ví dụ body JSON:

Thêm sách:

{
   "title":"Lập trình Java",
   "author":"Nguyễn Văn A",
   "year":2025,
   "quantity":10
}

Tạo thẻ mượn:

{
   "bookId":1,
   "borrowerName":"Trần Văn B",
   "borrowDate":"2026-05-19"
}

Trả sách:

{
   "returnDate":"2026-05-25"
}

Thiết kế trên tuân theo RESTful: dùng danh từ số nhiều (/books, /loans), dùng HTTP Method để biểu diễn hành động thay vì URL kiểu /addBook hoặc /deleteLoan.
