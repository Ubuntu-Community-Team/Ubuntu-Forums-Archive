---
title: "GRUB Error 17/15"
date: 2007-02-09
forum: General Help
---

### Post by DerDan on 2007-02-09
Hi, 
I had dual boot Ubuntu and Win XP. I used QtParted to format Ubuntu partition.
here is my HD partition:

WinXP            NTFS     Primary Active 40 GB
Linux              ext3      Primary           10 GB
Linux-Swap      ext3                           1.85 GB
Win                FAT32                           1.8 GB
free               free                             7.84 MB

Now I deleted Linux partions and the look alike of my current partition is 
WinXP            NTFS     Primary Active 40 GB
Win                FAT32                          14.08 GB
free               free                             7.84 MB

I commit QtPrated , next I restart system , I face GRUB 17/15  error..
Any Suggestions?

---

### Post by toGoq on 2007-02-09
You deleted your linux partiton, so Grub cannot find it. Here is a list of GRUB errror massages:
[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

---

### Post by logos34 on 2007-02-09
You need to overwrite grub with the windows bootloader.  

Boot from your winxp cd and enter 'R' to enter recovery console and then do the 'fixmbr' procedure.

---

