# โครงงานการสร้าง GUI Application โดยใช้ MATLAB App Designer

เนื่องจากรายวิชา Intro to Signals and Systems มีหัวข้อ Periodic Signals and Fourier Series Analysis คณะผู้จัดทำจึงเล็งเห็นความสำคัญของหัวข้อดังกล่าว และตัดสินใจนำมาประยุกต์ใช้กับโปรแกรม MATLAB App Designer โดยจัดทำเป็นโครงงานการสร้าง GUI Application โดยใช้ MATLAB App Designer เรื่อง การจำลองการทำงานของ graph generator ด้วย MATLAB App Designer เพื่อศึกษาวิธีการสร้างกราฟแบบต่าง ๆ ด้วย MATLAB App Designer โดยผู้ใช้งานแอปพลิเคชันสามารถปรับค่าแอมพลิจูด, ความถี่, Phase(Lagging/Leading), offset, time/div, volt/div และ plot กราฟให้อยู่ในรูปของ Square wave , Triangular wave , Sine wave , Sawtooth wave และ Full wave ได้

โดยเอกสารและความรู้ที่เกี่ยวข้องมีดังต่อไปนี้
- สมการของคลื่นชนิดต่างๆ
  - Square wave :
    X(t) =  4a*sin(k*Omega*t+p*k))/(pi*k)
    - a  controls the amplitude.
    - p  controls phase.
  - Sine wave :
    f(x) = ±a⋅sin(b(x+c))+d;
    - a  controls the amplitude.
    - d controls the vertical shift. 
    - b controls the horizontal stretch.
  - Triangular wave :
    X(t) = a/2 + ((-4*a)*cos(k*Omega*t+p*k))/(k*pi)^2
    - a controls the amplitude.
    - p  controls phase.
  - Sawtooth :
    X(t) = a/2 + (-a*sin(p*k+k*Omega*t))/(pi*k)
    - a  controls the amplitude.
    - p  controls phase..
  - Full wave :
    X(t) = 2a/pi + (-4acos(k*Omega*t+p*k))/(-4pi*(k^2))
    - a  controls the amplitude.
    - p  controls phase.
- Time/Div  (Time/Division)
  - ใช้สำหรับเลือกเวลาการกวาด ทําหน้าที่ขยายสัญญาณที่วัดเข้ามาโดยสามารถปรับคาบเวลา
- Volt/Div (Volts/Division)
  - ใช้สำหรับปรับขนาด (แอมพลิจูด) ของสัญญาณทางแนวตั้ง ทําหน้าที่ขยายสัญญาณที่วัดเข้ามาโดย สามารถปรับขนาดแรงดัน
- Offset
  - หากแอมพลิจูดเฉลี่ยของคลื่นเป็นศูนย์ คลื่นจะเกิดขึ้นในลักษณะที่แกน X มีค่าเป็นศูนย์สำหรับการกำหนดพิกัด (ค่าแกน Y) อย่างไรก็ตาม รูปคลื่นบางรูปถูกสร้างขึ้นเหนือแกน X นั่นเป็นเพราะแอมพลิจูดเฉลี่ยไม่ใช่ศูนย์ แต่มีค่ามากกว่าหรือน้อยกว่าศูนย์ เงื่อนไขนี้เรียกว่า DC offset
- Phase Shift
  - การเลื่อนกราฟไปทางซ้ายหรือขวาตามหน่วยองศา โดย Lagging จะเลื่อนกราฟไปขวา Leading จะเลื่อนกราฟไปซ้าย
  
  ![IMG_3099](https://user-images.githubusercontent.com/88374397/142239910-66e78404-7db2-4e19-b3fb-7c3ebf1743d3.jpg)

และการออกแบบการสร้างหน้าตาแอปพลิเคชันการจำลองการทำงานของ graph generator ดังต่อไปนี้

![IMG_3100](https://user-images.githubusercontent.com/88374397/142241751-32e3eca0-42d8-4354-9800-7911a59f8556.jpg)

- Waveform
  - เป็นการเลือกรูปแบบของกราฟโดยจะใช้ Dropdown menu เป็นส่วนช่วยในการแสดงข้อมูลของกราฟที่โปรแกรมสามารถสร้างออกมาได้ ซึ่งจะแบ่งเป็น Square wave, Triangular wave, Sine wave, Sawtooth wave และ Full wave
- Phase
  - เลือกใช้เป็น Dropdown menu เพื่อให้ผู้ใช้งานเลือกว่าต้องการให้โปรแกรมแสดงกราฟออกมาในรูปแบบของ Lagging หรือ Leading โดยช่องกรอกตัวเลขสามารถกรอกได้ตั้งแต่เลข 0 จนถึง infinity
- Offset
  - เป็นช่องกรอกตัวเลขซึ่งมีไว้กำหนดการแสดงผลการขึ้นลงของกราฟ
- Amplitude
  - เป็นช่องกรอกตัวเลขซึ่งมีไว้กำหนดเเอมพลิจูดของกราฟ
- Frequency
  - เป็นการใส่ความถี่ให้แก่กราฟ โดยจะมีช่องใส่ค่าตัวเลขและเลือกใช้ Dropdown menu เพื่อมีส่วนช่วยในการเลือกหน่วยที่ต้องการจะใช้งาน ซึ่งหน่วยดังกล่าวแบ่งออกเป็น x1 Hz, x10 Hz, x100 Hz, x1k Hz และ x10k Hz
- Time/Div
  - เป็นการปรับขนาดสเกลของเวลา ซึ่งมีการเลือกใช้ Knob เพื่อช่วยในการเลือกค่าที่ต้องการโดยจะมีค่าได้ตั้งแต่ 1 ถึง 10 และบ้างครั้งการปรับการใช้งานโดยการใช้ Knob อาจไม่สามารถแสดงค่าที่ผู้ใช้ต้องการได้อย่างแม่นยำ จึงตัดสินใจเพิ่มช่องในการใส่ค่าตัวเลขลงไปด้วยเช่นกัน และยังมีการเลือกใช้ Dropdown menu เพื่อให้ผู้ใช้สามารถเลือกหน่วยและขนาดของ Time/Div ที่ต้องการได้ โดยจะมีตัวเลือกดังต่อไปนี้ s, x1 ms, x10 ms, x100 ms, x10 us และ x100 us
- Volt/Div
  - มีการเลือกใช้ Knob เพื่อใช้ปรับขนาดของสเกลวัดแรงดัน โดยสามารถเลือกได้ตั้ง 1 ถึง 10 V และบ้างครั้งการปรับการใช้งานโดยการใช้ Knob อาจไม่สามารถแสดงค่าที่ผู้ใช้ต้องการได้อย่างแม่นยำ จึงตัดสินใจเพิ่มช่องในการใส่ค่าตัวเลขลงไปด้วยเช่นกัน และยังมีการเลือกใช้ Dropdown menu เพื่อให้ผู้ใช้สามารถเลือกหน่วยและขนาดของ Volt/Div ที่ต้องการได้ โดยจะมีตัวเลือกดังต่อไปนี้ x1 V, x10m V และ x100m V

ซึ่งทางคณะผู้จัดทำได้ดำเนินการตรวจสอบความถูกต้องและพบว่าแอปพลิเคชันการจำลองการทำงานของ graph generator สามารถทำงานได้อย่างถูกต้องสมบูรณ์โดยการเปรียบเทียบลักษณะของคลื่นกับเอกสารการเรียนรายวิชา Intro to Signals and Systems
  - Sine wave :
  
![IMG_3101](https://user-images.githubusercontent.com/88374397/142245524-1d4ec112-f18e-4778-9be4-9bbf068a50d4.jpg)

  - Square wave :
  
![IMG_3102](https://user-images.githubusercontent.com/88374397/142245546-6726dd46-495a-4177-93c4-ccd0255fd06c.jpg)

  - Sawtooth :
  
![IMG_3103](https://user-images.githubusercontent.com/88374397/142245566-a269b771-7612-4293-bc5a-43a632d33312.jpg)

  - Triangular wave :
  
![IMG_3104](https://user-images.githubusercontent.com/88374397/142245582-7ed2f734-119a-4b2d-9db2-a6464ba60c4d.jpg)

  - Full wave :

![IMG_3105](https://user-images.githubusercontent.com/88374397/142245594-dd9fb0a6-8910-42da-ac15-2fa06db6aaac.jpg)

และรูปดังต่อไปนี้จะเป็นตัวอย่างการทำงานบางส่วนของแอปพลิเคชันการจำลองการทำงานของ graph generator เมื่อทำการปรับค่าข้อมูลต่าง ๆ
  - Lagging 90 Degree :
  
 ![IMG_3106](https://user-images.githubusercontent.com/88374397/142247340-ecc5b3a1-39b4-45ba-b5bd-c5a8af1d5e16.jpg)

  - Leading 90 Degree :
  
![IMG_3107](https://user-images.githubusercontent.com/88374397/142247430-5735fde7-98e0-4bc0-80f9-e42d5a4a7ea5.jpg)

  - offset 1V :
  
![IMG_3108](https://user-images.githubusercontent.com/88374397/142247457-8462fa0e-3e4f-4efc-acc7-5e1bfa5104e3.jpg)

  - Amplitude 0.5 :
  
![IMG_3109](https://user-images.githubusercontent.com/88374397/142247474-ddac9497-64f7-4632-9a2c-58e715fd17b1.jpg)

  - Frequency 2 x1 Hz :
  
![IMG_3110](https://user-images.githubusercontent.com/88374397/142247501-cd17544a-b167-46ab-afdb-80a67a9f1a0d.jpg)

  - Frequency 2 x10 Hz :
  
![IMG_3111](https://user-images.githubusercontent.com/88374397/142247516-e0c137e5-ea18-47ed-bb2c-fddad8c641dd.jpg)

  - Time/Div 2 s :
  
![IMG_3112](https://user-images.githubusercontent.com/88374397/142247532-1682da0f-87ec-43e0-a0ff-90b46c31ffa5.jpg)

  - Volt/Div 2 x1 V :
  
![IMG_3113](https://user-images.githubusercontent.com/88374397/142247543-02fb250d-14eb-45e7-bef6-c77350975aa8.jpg)

  - Volt/Div 2 x10 mV :
  
![IMG_3114](https://user-images.githubusercontent.com/88374397/142247550-470b78dd-ec4d-412c-b8bf-366b97d65ea8.jpg)
