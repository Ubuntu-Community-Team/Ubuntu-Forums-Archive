---
title: "Trying to Install Unknown Web Cam"
date: 2008-02-21
forum: General Help
---

### Post by redstar1949 on 2008-02-21
I have a WidowPC laptop, model Venom 415D. It has an integrated webcam that does not appear in the list when I lsusb. I am not sure what the webcam is, and it does no get installed when I have tried camstream or easycam.

Where do I start?

---

### Post by redstar1949 on 2008-02-21
so I heard a rumor that it's a CCD camera if that means anything to anyone.

---

### Post by redstar1949 on 2008-02-21
Ok, my laptop manufacturer describes the windows driver as "Integrated PC Camera Driver (Ver. 5.7.2.004)"

and here is the Windows driver: [http://pro-star.com/drivers/EL80/PCCAM_572004.zip](http://pro-star.com/drivers/EL80/PCCAM_572004.zip)

Can anyone help me PLEASE? I'm really desperate here!

---

### Post by redstar1949 on 2008-02-21
I now heard it's a Chicony CMN5733 Camera and the laptop is a Compal EL80 but I'm not 100% that that is the exact cam odel, but it's worth a shot. Anyone got a linux driver?

---

### Post by sisco311 on 2008-02-21
pleas post the output from:
```
dmesg
``````
lsmod
```

---

### Post by redstar1949 on 2008-02-21
I have gotten it to work using the driver from linux-projects.org

---

### Post by redstar1949 on 2008-02-21
oh, and thanks again for your help!

---

