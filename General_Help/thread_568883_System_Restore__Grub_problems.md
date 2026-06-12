---
title: "System Restore / Grub problems"
date: 2007-10-06
forum: General Help
---

### Post by penguinjar on 2007-10-06
I had a dual boot XP/Ubuntu until I used the System Recovery CD that came with my laptop to wipe everything off (I need to get it serviced).  Now when I boot I get a grub error 22.  The recovery cd seems to have successfully wiped everything except the boot partition.  So now I can't boot to windows and I can't boot to linux, I can only use the LiveCD.  How do I fix the boot partition so grub is gone and I can load windows?

---

### Post by taurus on 2007-10-06
Go into the BIOS and make sure you have CD-ROM as a first bootable device.  Then, boot from the CD and install whatever you want.

---

### Post by penguinjar on 2007-10-06
I can boot from the windows cd but it only gives me one option, which is to restore, and I did that but it didn't help because I can't get past grub.

---

### Post by taurus on 2007-10-06
Do you have Windows CD?  You need to restore your MBR so Windows would boot from a harddrive.

---

### Post by penguinjar on 2007-10-06
I don't have a Windows CD, only a recovery cd that came with the computer.

---

### Post by taurus on 2007-10-06
Is Windows still on the harddrive or did you just wipe everything off your harddrive?

---

### Post by penguinjar on 2007-10-06
I'm not sure, I didn't explicitly delete it myself before using the cd,  The cd said it would erase all of my data and restore the system to the original condition.  It also said it was going to erase what was on the other partitions, which was the linux stuff at the time.

---

### Post by taurus on 2007-10-06
Do you still have a Ubuntu LiveCD around?  Try booting with it and see if Windows still resides on the harddrive.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by penguinjar on 2007-10-06
Yeah I have the LiveCD, that's what I'm using now.

```

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

```

---

### Post by taurus on 2007-10-06
Try

```
sudo mkdir /media/sda1
sudo mount -t ntfs /dev/sda1 /media/sda1
sudo ls- la /media/sda1
```
Post the output of the last command here to see if Windows is still resided on /dev/sda1.

---

### Post by penguinjar on 2007-10-06
Here it is:

```
ubuntu@ubuntu:~$ sudo ls -la /media/sda1
total 392
dr-x------ 1 root root  16384 2004-12-17 22:48 .
drwxr-xr-x 3 root root     80 2007-10-06 18:55 ..
dr-x------ 1 root root   4096 2001-04-04 09:08 ARCSOFT
dr-x------ 1 root root   4096 2004-11-15 23:46 ARCSOFT_TRIAL
-r-------- 1 root root      0 2004-11-16 02:28 AUTOEXEC.BAT
-r-------- 1 root root    210 2004-11-17 03:34 boot.ini
-r-------- 1 root root      0 2004-11-16 02:28 CONFIG.SYS
dr-x------ 1 root root      0 2001-04-04 09:52 DOCS
dr-x------ 1 root root   4096 2004-11-16 02:32 Documents and Settings
dr-x------ 1 root root      0 2004-11-16 04:22 EZFirewall
-r-------- 1 root root      0 2004-11-16 02:28 IO.SYS
-r-------- 1 root root    823 2004-11-16 05:30 IPH.PH
-r-------- 1 root root      0 2004-11-16 02:28 MSDOS.SYS
-r-------- 1 root root  47564 2004-08-04 12:00 NTDETECT.COM
-r-------- 1 root root 250032 2004-08-04 12:00 ntldr
dr-x------ 1 root root  12288 2004-12-11 19:51 Program Files
dr-x------ 1 root root  12288 2004-12-18 05:24 SYSPREP
dr-x------ 1 root root      0 2004-11-16 05:23 TOSHIBA
dr-x------ 1 root root  36864 2004-12-15 07:14 WINDOWS
dr-x------ 1 root root   4096 2004-11-17 02:51 WORKSSETUP
ubuntu@ubuntu:~$ 

```

---

### Post by taurus on 2007-10-06
You probably need to download a boot disk for your Windows.  Then, boot from it and overwrite MBR, removing GRUB, so Windows will boot each time you turn it on.

Probably have to do it from another machine since you can't boot your machine right now until your recover MBR.

[http://freepctech.com/pc/002/files010.shtml](http://freepctech.com/pc/002/files010.shtml)

---

### Post by confused57 on 2007-10-06
Super Grub Disk may be another option to reinstall Windows IPL to the mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7 Mb)

or a Win98SE boot floppy, as taurus suggested:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by penguinjar on 2007-10-07
Thanks guys,
I made a Super Grub CD and ran fixmbr off that, and now everything works fine.
I appreciate the help!

---

