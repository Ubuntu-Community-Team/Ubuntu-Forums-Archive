---
title: "External Hard Drive Problem"
date: 2008-05-23
forum: General Help
---

### Post by GR3EN on 2008-05-23
i just switched over from windows to ubuntu today and all was well untill i plugged in my external hard disk drive with alot of information on it i need. when i plugged it in i got this message: 

[img]http://i31.tinypic.com/ru1dsg.png[/img]

i tried to follow the directions but didnt work. i know it mentions windows but im not using it in any way no dual boot etc. remember im new to ubuntu so if anyone could help i would greatly appreciate it.

Thanks,

GR3EN

---

### Post by graham-cracker on 2008-05-23
I ran into this problem once before, and running something similar to:

sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force

worked for me. What does the command output when you run it?

---

### Post by GR3EN on 2008-05-23
mike@mike-desktop:~$ sudo mount -t ntfs-3g /dev/sbd1 /media/disk -o force
ntfs-3g: Failed to access volume '/dev/sbd1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

---

### Post by graham-cracker on 2008-05-23
Did you try sdb1 or sbd1. It should be /dev/sdb1 as in :

sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force

If that doesn't work, what is the output of:

dmesg

after you plug in your hard drive (and after the error pops up). There will probably be quite a few lines (a few hundred).

---

### Post by GR3EN on 2008-05-23
yes i did just type it wrong. thanks alot!! i really appreciate it. i haave alot of stuff on there i needed. your a life saver.

---

### Post by graham-cracker on 2008-05-23
No problem, I'm just glad to help.

---

