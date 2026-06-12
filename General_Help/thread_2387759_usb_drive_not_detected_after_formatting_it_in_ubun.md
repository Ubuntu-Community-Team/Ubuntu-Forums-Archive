---
title: "usb drive not detected after formatting it in ubuntu"
date: 2018-03-23
forum: General Help
---

### Post by ghost87 on 2018-03-23
I am using ubuntu 16 LTS. Recently i have tried formatting a usb drive in it and after that it is not detectable by any other OS. Hardware must be working because whenever i try to mount it, it shows the indicator light but it not detectable. 
I have already used "sudo fdisk -l " and is still undetectable.Please help.

---

### Post by Impavidus on 2018-03-23
What file system did you use? Maybe the other OS doesn't support that file system.

---

### Post by yancek on 2018-03-23
Also, how did you format it, from a terminal with mkfs command, using GParted or similar software?  If fdisk doesn't show it, does it appeara in the BIOS?

---

