---
title: "Help with NTFS internal drive."
date: 2018-11-12
forum: General Help
---

### Post by 1488-based on 2018-11-12
Hello I have a data drive inside my computer that is an NTFS format drive that I can no longer modify the data on. I can read data but do nothing else. It worked perfectly fine with Ubuntu 18.04 LTS (full read/write) but I upgraded to Ubuntu 18.10 and now have this issue. When I go into the disk properties it says all users and root have full read/write access. If i open Nautilus using sudo Nautilus in the Terminal the ability to even see the drive is gone.

The Ubuntu system drive is a separate physical disk, the drive in question has only one partition and has nothing but personal files on it.

I want to move my files off to an external data disk and reformat this internal one into ext4 to use within my system but I would like to sort and delete some data and move the rest off without just making a copy to the new disk, the disk is 1Tb.

May someone please help me with is issue if they can.


Update: I was able to fix the issue by running sudo ntfsfix /dev/sdb1 in a Terminal and fixed the problem right away. :)

cheers.

---

### Post by HermanAB on 2018-11-12
You need to run chkdsk with MS Windows.  

You could install Windows in a virtual machine with KVM or Virtualbox.

---

### Post by mastablasta on 2018-11-12
> **1488-based said:**
>  If i open Nautilus using ***sudo Nautilus*** in the Terminal the ability to even see the drive is gone.

Bad idea. use sudo -H instead

> 

The Ubuntu system drive is a separate physical disk, the drive in question has only one partition and has nothing but personal files on it.

I want to move my files off to an external data disk and reformat this internal one into ext4 to use within my system but I would like to sort and delete some data and move the rest off without just making a copy to the new disk, the disk is 1Tb.

May someone please help me with is issue if they can.

cheers.
if the check disk doesn't repair it, then something is wrong with the drive itself, not the file system. i would first make a copy using clonezilla or similar tool (empty space is compressed at the image).

checkdisk can be done using a version of freedos that containes NTFS checker.
another option is to use recovery disk downloaded from MS: [https://superuser.com/questions/193899/how-to-run-chkdsk-if-i-cant-boot-to-windows](https://superuser.com/questions/193899/how-to-run-chkdsk-if-i-cant-boot-to-windows)
various reputable antivirus companies also offer recovery disks for free that will run chkdsk if needed.


to establish if the drive is good or not you need to run S.M.A.R.T. tools. tool made for specific disk drive are often windows only, however a set of such tools can also be found on for example Ultimate boot CD. you boot the CD and run the tool for your disk.  
since you have a working system disk you might want to look into smartmon tools first: [https://www.smartmontools.org/](https://www.smartmontools.org/)

they are in repositories.: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

you might want to add a GUI like [FONT=arial]GSmartControl [/FONT]to it, though that is not necessary.

---

### Post by 1488-based on 2018-11-12
I have Windows XP and Windows 7 installed in Virtual Box but they can not see the NTFS drive I have the issues with, only the Virtual Disk C drive. Do you know how i can mount it in win 7 virtual box? It is mounted in the host system but not guest system.

---

### Post by 1488-based on 2018-11-12
The disk SMART status shows it is 100% healthy. I did a hardware scan in my machine BIOS and shows healthy with no errors. I do not have a computer with Windows natively running on it only virtual machines but Windows VM can not see the drive? Safe to say the disk is physically ok and it's an NTFS file system error caused at one stage by Windows 10 back when i was dual booting maybe.

---

### Post by HermanAB on 2018-11-12
The easiest way is with a special Windows boot disk:
[http://www.boot-disk.com/check_disk.htm](http://www.boot-disk.com/check_disk.htm)
[http://www.boot-disk.com/download.htm](http://www.boot-disk.com/download.htm)
[https://www.raymond.cc/blog/running-a-check-disk-with-an-easy-to-use-interface/](https://www.raymond.cc/blog/running-a-check-disk-with-an-easy-to-use-interface/)

---

