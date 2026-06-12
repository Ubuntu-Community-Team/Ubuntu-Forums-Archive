---
title: "Problems at starting Ubuntu after installing Wubi"
date: 2008-06-08
forum: General Help
---

### Post by sportfreak on 2008-06-08
hello,

i was very happy to see, there is Wubi to install ubuntu.
I downloaded the newest version and installed it from my Windows XP Prof.
My Computer is a Athlon 1200XP with 1 Harddisk (120 GB)and 4 Partitions. On the first i have Windows 2000 Prof and on the second Windows XP Prof.
I installed Wubi to C:\, because i can't choose anyting else at the installer window.

the installation was gone without any errors. After restarting i choosed "Ubuntu" from the menu of my operating systems.

Then i get the following screen:
###########################
Try (hd0,0): non-MS: skip
Try (hd0,1): non-MS: skip
Try (hd0,2): Extended: invalid or null
Try (hd0,3): non-MS: skip
Try (fd0): invalid or null
Error: Cannot find GRLDR in all devices. Press Ctrl+Alt+Del to restart
###########################

i searched in web for many hours and only find "Booting problems: Error 15, file not found" on [https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

i hoped to solve the problem using that, but the folder c:\ubuntu\disks\boot\grub\ is empty and there is no menu.lst.

I find it instead on C:/ubuntu/install/boot/grub/ and an other on C:/ubuntu/winboot, but the content of that file has no "root (hdX,Y)/ubuntu/disks" or "#groot=(hdX,Y)/ubuntu/disks" (i don't understand where this should be in menu.lst, in my files there is nothing like that).

I also tried to copy the C:/ubuntu/install/boot/grub/menu.lst to in the rootpath of all partitions, but the problem isn't solved.

i would be very to to get help.

---

### Post by sportfreak on 2008-06-08
I also read the thread [http://ubuntuforums.org/showthread.php?t=782663&highlight=GRLDR&page=2](http://ubuntuforums.org/showthread.php?t=782663&highlight=GRLDR&page=2) which seems to be the same problem. but this does not resolve my problem.

here is, what fstest tells me. i hope, it will help to find an answer for my problem.

==> fstest info C:\
*******
version: 1.0 build 3
part_base: 0x3F (0M)
part_leng: 0x1D4EFFA (15005M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x20
*******

===> fstest inode C:\wubildr
*******
Type: File
Attr:
  $STANDARD_INFORMATION (0x10) (r,sz=72)
  $FILENAME (0x30) (r,sz=80)
    wubildr
  $DATA (0x80) (nr,sz=186043)
    5627704+368
********

===> fstest comp C:\wubildr
********
File size : 186043
Comparing 
Succeed
********

please help.

---

### Post by sportfreak on 2008-06-08
i think it could be something wrong with boot.ini

i looked at it after reading [http://ubuntuforums.org/showthread.php?t=780478&highlight=GRLDR](http://ubuntuforums.org/showthread.php?t=780478&highlight=GRLDR)

there is written
###########################
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect
c:\wubildr.mbr="Ubuntu"
##########################

I uninstalled and installed Wubi two times and nothing of my problems had changed

---

