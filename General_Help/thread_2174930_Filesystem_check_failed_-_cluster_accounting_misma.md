---
title: "Filesystem check failed - cluster accounting mismatch"
date: 2013-09-16
forum: General Help
---

### Post by yaro2 on 2013-09-16
Hello !

I had win 7 where I installed ubuntu 12.04 using wubi. It all worked fine for long time, and one day the harddrive stopped working.

I managed to connect the drive externally to a different machine.

In ubuntu the drive mounts, and shows the files. If I run 

```
sudo ntfsfix /dev/sdb3
```

it says - successfull.

The Gparted shows warning sign - Filesystem check failed - cluster accounting mismatch, and suggests running chkdsk. 

The problem is that when connect the drive to windows 7 - it says that the drive needs to be reformated. And does not show the volume letter.

So, the disk is formated NTFS and I can see the files in Ubuntu, but not from Windows.

Ideas how to fix it from Ubuntu ?

Thank you !
Yaro

---

### Post by VMC on 2013-09-16
Linux doesn't have any NTFS utilities other than the checking type. If your wanting data off the disk then it looks like Linux is the only way. What are you trying to achieve, to fix the Windows NTFS drive and boot Windows from the drive? If so, then maybe Windows Repair Disk will fix the NTFS errors.

---

### Post by yaro2 on 2013-09-17
VMC, thank you for the reply. What is strange for me is that Ubuntu can access to the drive, and I can copy the files and write files. While Windows says that the drive needs to be formatted. Ubuntu says that the drive is NTFS .... 
Bizarre ...

---

