---
title: "first harddrive w/XP will not boot, Ubuntu 7. will not start."
date: 2008-05-23
forum: General Help
---

### Post by jlo-nypr on 2008-05-23
I have a HP Compaq Prolient AMD processor desk top.  It came with a 80 gb hard drive.  I reformated to NTFS with XP.  I bought a new 340 gb drive placed on second channal installed Ubuntu.  My XP crashed (XP)did not boot.  Trying to fix it by reading other postings deleted my Ubuntu boot to my second drive.  :(

I need to get my ubuntu to work.  I did copy my XP files to the Ubuntu hard drive, but it is all Lenux file system.  I was at one point being able to get into Ubuntu, but now I cannot.  By the way, I tried reformating my first XP drive but get errors trying to reformat in both NTFS and Ubuntu.

If I boot to the cd, I can read both drives.  Help!!  Please!!:confused:

---

### Post by TeoBigusGeekus on 2008-05-23
Boot with a live cd and post us the results of 
```
sudo fdisk -l
```
(-L)
Also, locate the path to /boot/grub/menu.lst and post us its contents
```
gksudo gedit /path/to/boot/grub/menu.lst
```

---

