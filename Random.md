 - Sau khi giải nén và đọc file chall.py, mình nhận thấy:
   + Khởi tạo seed là giá trị ngẫu nhiên trong khoảng 0 đến 10000
   + Khởi tạo flag và mã hóa flag qua 1337 vòng lặp bằng cách thực hiện XOR từng byte của flag với 1 số ngẫu nhiên trong khoảng 0 đến 255
   + In kết quả dưới dạng chuỗi hex: 0203e2c0dd20182bea1d00f41b25ad314740c3b239a32755bab1b3ca1a98f0127f1a1aeefa15a418e9b03ad25b3a92a46c0f5a6f41cb580f7d8a3325c76e66b937baea
- Hưởng giải quyết:
   + Nếu tìm được seed thì có thể tiến hành giải mã bằng cách XOR từng byte của chuỗi hex với 1 số ngẫu nhiên trong khoảng 0 đến 255
   + Mình thực hiện bruteforce để tìm ra seed, sau đó thử hết tất cả giá trị trong khoảng 0 đến 255 để tìm ra flag.
- Code:

![image](https://github.com/user-attachments/assets/2ba62b0c-f7f1-4297-9e24-25e18187f87e)

- Phân tích:
  + Khởi tạo biến en_data để lưu giá trị của flag đã được mã hóa sau khi chuyển từ hex về byte
  + ![image](https://github.com/user-attachments/assets/6b8b66f3-87a3-4e39-be78-874c5a708ee6)
      * Thử tất cả các giá trị của seed trong khoảng 0 đến 10000
      * Thiết lập bộ sinh só ngẫu nhiên cho seed
      * test_data = list(en_data): Khởi tạo mảng test_data từ chuỗi en_data ban đầu để đem đi thử giải mã
  + ![Screenshot 2024-12-13 105141](https://github.com/user-attachments/assets/058add98-190a-4a70-b453-a6896f5492cd)
      * Tiến hành giải mã ngược bằng cách XOR qua 1337 vòng lặp
      * Khởi tạo mảng rd_values gồm các số ngẫu nhiên trong khoảng 0 đến 255 có độ dài bằng với test_data
      * Thực hiện phép XOR
  + ![image](https://github.com/user-attachments/assets/ef646efb-3c9e-4ff6-80c8-8a4000a36b34)
      * Sau khi thoát khỏi vòng lặp, chuyển test_data về byte và kiểm tra xem có kí tự "{" trong chuỗi byte đó hay không, nếu có thì in ra màn hình và kết thúc chương trình, nếu không thì tiếp tục chương trình




