เริ่มต้น Docker คือ ?


~ ทำไม DOCKER ?
 ปัญหาใหญ่ในการจัดการจัดการ environment ในการพัฒนา application หรือ software ต่างๆ เป็นสิ่งที่จุกจิกแล้วรู้ได้ยาก เช่น app นี้อาจจะ run ได้บน เครื่องๆนึง แต่ อีกเครื่องกลับรันไม่ได้ เฉย เซ็ง… 
การ มี application เดียวกัน ที่ต้อง set dependencies ของ app ที่ต้องใช้ ในทุก เครื่องนั้นมัน ไม่ scalable ปกติ การ สร้าง VM/OS ใหม่ต้องเสีย พื้นที่มากมายใน คอมพิวเตอร์/server ซึ่งถ้าอยาก deploy app ที่ใช้ version ที่ต่างจาก VM เครื่องนั้น ก็ต้อง add VM เพิ่ม
มาดู กันว่าทำไม Docker ถึงดีกว่า …
~เปรียบเทียบ : ถ้าเป็น VM ทุก App จะรันบน OS ของตัวเองแล้ว common library จะไม่สามารถ share กันได้
Portabilty คือ key สำคัญของ docker ในการ develop และ ship application ได้ง่ายดาย เพราะสามารถกำหนด dependencies ทุกอย่างใน image แล้ว สามารถรันบนเครื่องที่มี docker ได้ทุกเครื่อง 100% 
Efficiency  ความเร็วในการ รัน application บน container สามารถทำได้ไวกว่า VM และ การใช้ CPU, RAM, Space บนเครื่องน้อยกว่าการ ใช้ VM มาก เพราะ VM ต้อง install full OS.
~ Docker ประกอบด้วย
เคยสงเกตุไหมว่า โลโก้ Docker น้องปลาวาฬเกยตื้นที่แบกตู้ container 
Container
Container คือ 1 app ที่รันจาก image
Unit ของ software ตัวนึง

Image
เป็น app สำเร็จรูปที่สามารถ นำไป run ได้
ไม่สามารถ แก้ไขได้ read-only
มีหลาย version/tag ในการเลือกใช้ได้
มี Layer ที่เป็น ส่วนประกอบของหลายๆ

~ Docker Image เก็บไว้ในไหน ? 
Registry Provider เช่น Docker Hub หรือ Docker Cloud เป็น public registry ที่สามารถทุกคนสามารถเข้าไปดึง image มาใช้ได้
สามารถ เก็บ image ไว้เป็น private ได้เหมือนกัน ( Docker Hub free 1 repo )
สำหรับบาง Enterprise ที่อยาก host registry ของตัวเอง อาจจะใช้การ host บน cloud เช่น EC2 Container Registry หรือ host บน server ตัวเองโดยใช้ Artifactory, GitLab

~ Workflow Docker
// Sequence Diagram
~ ทำงานกับ docker 
Developer ทำการเขียน Application และ test
สร้าง Dockerfile ใช้เป็นคำสั่งในการสร้าง image 
สร้าง Image และ กำหนด version
ทำการ publish Image ไปเก็บไว้บน registry
ทำการ deploy 
วนไปเรื่อยๆ



การ Install
https://docs.docker.com/engine/install


References


https://www.datadoghq.com/docker-adoption/
