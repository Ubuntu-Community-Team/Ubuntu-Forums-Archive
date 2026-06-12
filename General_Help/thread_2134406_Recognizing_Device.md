---
title: "Recognizing Device"
date: 2013-04-11
forum: General Help
---

### Post by koccer on 2013-04-11
Hi all;
I want to learn how can i fasten usb port to device path? Like this on one usb port must always take a sdb1 which device pluged. Another usb port take sdb2 like this...

In my search i wrote udev rule and another way i wrote fstab file sentences but i can not take any effect which i want to do.

Any body know how can i do it?

---

### Post by fantab on 2013-04-11
/dev/sdb1 and/or /dev/sdb2 are partition numbers with belong to /dev/sdb. The separate drives will be /dev/sda, /dev/sdb/, dev/sdc and so on. Lets say your HDD is /dev/sda, then when a USB is plugged in (in any USB port) it will be /dev/sdb, now when you plug in another USB Drive (in any USB port), it will be know to the system as /dev/sdc and so on. 

AFAIK, I don't think you can "fasten usb port to device path".
Perhaps someone else here will be able to confirm this...

---

### Post by koccer on 2013-04-12
Yes i am sorry for my mistake i wrote it wrong. 
I want that one usb port always will take sdb second one will take sdc and so on.
In my search i found that one thumbdrive can take a same name if you change fstab file. But i can not do it for this way what i want.

---

