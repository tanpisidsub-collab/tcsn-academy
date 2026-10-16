คู่มือติดตั้งเว็บไซต์ใหม่: TCSN Academy — แบบทดสอบและเกียรติบัตร

เว็บไซต์นี้เป็นเว็บใหม่แยกจากเว็บไซต์ TCSN เดิม ไม่ต้องนำไปทับ Repository เก่า

ไฟล์ในชุดนี้:
- index.html: หน้าเว็บใหม่ ระบบสมาชิก คลังแบบทดสอบ ทำข้อสอบ ตรวจคะแนน ประวัติ และตรวจสอบเกียรติบัตร
- certificate-template.png: ภาพเกียรติบัตรที่ผู้ใช้ส่งมา ใช้เป็นพื้นหลังตอนสร้าง PDF
- firestore.rules: กฎเริ่มต้นของ Firestore
- README_TH.txt: คู่มือฉบับนี้

วิธีเผยแพร่เว็บใหม่ด้วย GitHub Pages:
1. เข้า GitHub แล้วสร้าง Repository ใหม่ เช่น tcsn-academy (ตั้งเป็น Public ได้ถ้าต้องการใช้ GitHub Pages ฟรี)
2. อัปโหลด index.html และ certificate-template.png ไว้ในโฟลเดอร์รากของ Repository
3. ไปที่ Settings > Pages > Build and deployment เลือก Deploy from a branch แล้วเลือก main และ / (root)
4. เปิด Firebase Console แล้วสร้างหรือเลือก Firebase project สำหรับเว็บใหม่นี้
5. เปิด Authentication > Sign-in method > Email/Password
6. ตรวจสอบ firebaseConfig ใน index.html ให้เป็นค่าของ Firebase project ที่ต้องการใช้
7. ใน Authentication > Users ให้สร้าง/สมัครบัญชีเจ้าของเว็บและคัดลอก UID
8. แก้ค่า ADMIN_UID ใน index.html และ REPLACE_WITH_YOUR_FIREBASE_UID ใน firestore.rules ให้เป็น UID เดียวกัน
9. นำเนื้อหา firestore.rules ไปวางใน Firestore Database > Rules แล้ว Publish
10. เปิด URL GitHub Pages แล้วเข้าสู่ระบบด้วยบัญชีเจ้าของเว็บ เพื่อสร้างแบบทดสอบจากเมนูหลังบ้าน

ข้อควรทราบ:
- ไฟล์นี้เป็นเว็บใหม่แยกต่างหาก ไม่ได้เปลี่ยนแปลงเว็บไซต์เดิมของคุณ
- ก่อนเผยแพร่จริง ควรตรวจสอบ Firebase config และทดสอบกฎความปลอดภัย
- การตรวจคะแนนในรุ่นเริ่มต้นยังทำฝั่งเบราว์เซอร์ จึงยังไม่เหมาะกับใบรับรองที่ต้องการความปลอดภัยระดับทางการ ควรย้ายการตรวจคำตอบไปยัง Firebase Cloud Functions และแยกเฉลยไม่ให้ผู้สอบอ่านได้
- การสร้าง PDF/QR ใช้ไลบรารีจาก CDN ต้องเชื่อมต่ออินเทอร์เน็ต
