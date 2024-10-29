command to run file hadoop jar "C:\jar\Kmeans.jar" /btl-input/databtl.csv /btl_output
quy trinh lam sach du lieu
1. Chuyển đổi và Kiểm tra giá trị
Chuyển đổi dữ liệu: Các giá trị từ dữ liệu thô được chuyển đổi từ chuỗi (String) sang kiểu số (double). Các cột bao gồm:

Age (tuổi): data[2]
Hypertension (tăng huyết áp): data[3]
Heart Disease (bệnh tim): data[4]
BMI: data[9]
Average Glucose Level (mức đường huyết trung bình): data[8]
Xử lý giá trị bị thiếu: Nếu BMI có giá trị là "N/A" (không có giá trị), ta đặt nó thành 0 để đảm bảo mã không bị lỗi khi gặp giá trị thiếu.

Kiểm tra tính hợp lệ của dữ liệu: Sau khi chuyển đổi, mã kiểm tra xem các giá trị có nằm trong phạm vi hợp lý không:

Age (tuổi) phải lớn hơn 0.
BMI và Average Glucose Level phải lớn hơn hoặc bằng 0.
Nếu bất kỳ giá trị nào không đạt yêu cầu (không hợp lệ hoặc không nằm trong phạm vi), dòng dữ liệu đó sẽ bị bỏ qua bằng cách trả về null.

2. Chuẩn hóa Dữ liệu (Normalization)
Dữ liệu thô sẽ được chuẩn hóa để đưa về một phạm vi nhất định. Điều này giúp cân bằng mức độ ảnh hưởng của các thuộc tính khi tính toán khoảng cách giữa các điểm và các tâm cụm.
Age: chia cho 100 (giả sử tuổi nằm trong khoảng 0-100).
BMI: chia cho 50 (giả sử BMI nằm trong khoảng 0-50).
Average Glucose Level: chia cho 300 (giả sử mức đường huyết trong khoảng 0-300).
3. Trả về dữ liệu đã làm sạch
Nếu dữ liệu là hợp lệ, một mảng số thực (mảng double) chứa các giá trị age, hypertension, heartDisease, bmi, và avgGlucoseLevel sẽ được trả về.
Nếu không hợp lệ, mã trả về null để bỏ qua dòng dữ liệu đó trong hàm map.
