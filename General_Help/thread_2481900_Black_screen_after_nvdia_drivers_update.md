---
title: "Black screen after nvdia drivers update"
date: 2022-12-12
forum: General Help
---

### Post by alo12 on 2022-12-12
Hi, after update of the nvidia drivers i get a black screen after ubuntu 20.04 boot. i have tried the recovery mode but when i press resume i get the black screen again. is there any changes i can to to the files of my hard isk through a live usb in order to fix the problem? Thank you in advance.

---

### Post by grahammechanical on 2022-12-12
Recovery mode>Resume should load to a desktop using an open source video driver and not the proprietary Nvidia driver. So, it should have solved the issue as far as getting to a working desktop environment. 

You could try Advanced Options for Ubuntu and load the earlier kernel. There should be a recovery mode for that kernel. If you get to a desktop you could open Software and Updates>Additional Drivers and see if you are offered more than one additional Nvidia driver and choose an earlier Nvidia driver.

You could also try running Ubuntu on X-Server rather than Wayland.

Regards

---

### Post by alo12 on 2022-12-12
thank you fro your response, ia have tried both but i get the black screen again... in both case when i choose resume i get the black screen, i have tried all options to the adavanced options menu

---

