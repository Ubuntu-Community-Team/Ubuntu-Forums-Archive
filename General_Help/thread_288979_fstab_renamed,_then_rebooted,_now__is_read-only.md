---
title: "fstab renamed, then rebooted, now / is read-only"
date: 2006-10-30
forum: General Help
---

### Post by stiankarlsen on 2006-10-30
So, here's my problem, I renamed fstab to fstab.bak, because I wanted to create an all new fstab file, problem is that I got a bit distracted and started editing the fstab.bak file, and the fstab file is now just an empty blank file. So when I boot, the file system is set as read-only.

What the hell do I do?

In recovery mode, I tried "umount /dev/sda1 -t ext3 /" and it tells me that sda1 has been unmounted, but when I run "mount /dev/sda1 -t ext3 /", it tells me that the device is busy or already mounted.

Im so stuck, what do I try next?

Really appreciate any help I can get.

Stian Karlsen.

---

### Post by konst88 on 2006-10-30
run livecd, mount you / partiton, and edit the fstab.

---

### Post by jocko on 2006-10-30
tried booting a live cd? from there you should be able to mount your partition and replace the empty file.

---

### Post by stiankarlsen on 2006-10-30
Of course, how did i not think of that.](*,) 

Appreciate it.

---

