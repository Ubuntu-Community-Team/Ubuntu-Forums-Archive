---
title: "SCSI Removed in installation now want it back?"
date: 2006-12-16
forum: General Help
---

### Post by ambar on 2006-12-16
hello everybody

Can u please help with a small problem? 
i have 2 hard drives :
1: 80gb sata : with 4 partitions of 20gb each(**each fat32)**
2: 20gb Pata : with a 9gb partition on which ubuntu is installed **( ext3)**
                           with a 12gb partition on which nothing  is installed ;i use it for storing data**(fat32)**

Problem:
i removed the option of installing any folder like (/media/sda1 , /media/sda2.....4)) on sata while installing ubuntu.hence the drives of sata became** invisible. **
now i want them to be **visible** so that i can use the data i have on that drives(like movies and pdfs)

tell me if i am not clear.
thank you
ambar

---

### Post by dcstar on 2006-12-16
> **ambar said:**
> hello everybody

Can u please help with a small problem? 
i have 2 hard drives :
1: 80gb sata : with 4 partitions of 20gb each(**each fat32)**
2: 20gb Pata : with a 9gb partition on which ubuntu is installed **( ext3)**
                           with a 12gb partition on which nothing  is installed ;i use it for storing data**(fat32)**

Problem:
i removed the option of installing any folder like (/media/sda1 , /media/sda2.....4)) on sata while installing ubuntu.hence the drives of sata became** invisible. **
now i want them to be **visible** so that i can use the data i have on that drives(like movies and pdfs)

tell me if i am not clear.
thank you
ambar

You will need to manually edit your /etc/fstab file to mount these partitions, do a forum search for the various HOWTOs on accessing hard drives.

---

### Post by ambar on 2006-12-16
ya thank you i got it using a howto :)

---

