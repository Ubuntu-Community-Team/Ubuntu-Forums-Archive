---
title: "hard disks: difference in speed between 5400 and 7200 rpm?"
date: 2007-09-06
forum: General Help
---

### Post by megamania on 2007-09-06
My current hard disk set up for my desktop computer is as follows:
-	one 160gb disk(7200rpm, Maxtor Sata): 1gb swap, 7gb Ubuntu, the rest /home
-	one 160gb disk(7200rpm, Maxtor Ide): 1gb swap, 7gb another distro, the rest backup of home

I just bought a second-hand 60gb (Maxtor Ide) hard disk which is 5400rpm.

It would be convenient for me to install the operating systems on this hard disk and use the other two for data, but I’m wondering if the difference in speed between 5400rpm and 7200rpm would be noticeable (boot up time and general use) considering that only the o.s. would reside there, while the data would be on the faster disks.

If the difference is substantial, I'll have to study a different layout.

Any experiences on this?

---

### Post by eggdeng on 2007-09-06
Considering that the disk with the OSs on it is the one which will *always* be in use, I don't think it makes much sense to use the slowest one for this purpose. I would expect a significant performance hit. I'd put the OSs on one of the faster disks, media files and files you frequently use on the second of these and keep the slower disk for smaller files like text files, or seldom used stuff like back-ups.

---

### Post by martijn hoekstra on 2007-09-06
As an additional comment, if you do make use of a swap partition, make sure that that one is on the fastest drive you have. Seek/access time is the most important there.

---

### Post by megamania on 2007-09-07
Well,

I was expecting a slowdown in boot-up time, but not a significant impact on normal use. I'll have to study a different solution then...

Thanks a lot for your suggestions.

---

