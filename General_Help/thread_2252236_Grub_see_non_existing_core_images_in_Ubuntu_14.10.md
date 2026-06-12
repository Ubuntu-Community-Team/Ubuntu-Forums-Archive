---
title: "Grub see non existing core images in Ubuntu 14.10"
date: 2014-11-10
forum: General Help
---

### Post by i12 on 2014-11-10
Grub see
Generating grub configuration file ...
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; linux: /boot/vmlinuz-3.16.0-24-generic
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; initrd: /boot/initrd.img-3.16.0-24-generic
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; linux: /boot/vmlinuz-2.6.38-16-generic
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; initrd: /boot/initrd.img-2.6.38-16-generic
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; linux: /boot/vmlinuz-2.6.38-8-generic
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; &#1086;&#1073;&#1088;&#1072;&#1079; initrd: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; Windows NT/2000/XP (loader) &#1085;&#1072; /dev/sdb1
&#1053;&#1072;&#1081;&#1076;&#1077;&#1085; MS-DOS 5.x/6.x/Win3.1 &#1085;&#1072; /dev/sdb5

ls -l /boot...
```
natha@natha-GA-MA785GM-US2H:~$ ls -l /boot
&#1080;&#1090;&#1086;&#1075;&#1086; 71320
-rw-r--r-- 1 root root   736214 &#1089;&#1077;&#1085;&#1090;.  6  2012 abi-2.6.38-16-generic
-rw-r--r-- 1 root root   735445 &#1072;&#1087;&#1088;.  11  2011 abi-2.6.38-8-generic
-rw-r--r-- 1 root root  1207071 &#1086;&#1082;&#1090;.  28 16:47 abi-3.16.0-24-generic
-rw-r--r-- 1 root root   137332 &#1089;&#1077;&#1085;&#1090;.  6  2012 config-2.6.38-16-generic
-rw-r--r-- 1 root root   137319 &#1072;&#1087;&#1088;.  11  2011 config-2.6.38-8-generic
-rw-r--r-- 1 root root   171704 &#1086;&#1082;&#1090;.  28 16:47 config-3.16.0-24-generic
drwxr-xr-x 6 root root    12288 &#1085;&#1086;&#1103;&#1073;.  4 10:28 grub
-rw-r--r-- 1 root root 12876514 &#1085;&#1086;&#1103;&#1073;.  2 21:31 initrd.img-2.6.38-16-generic
-rw-r--r-- 1 root root 12876489 &#1085;&#1086;&#1103;&#1073;.  2 21:09 initrd.img-2.6.38-8-generic
-rw-r--r-- 1 root root 20398102 &#1085;&#1086;&#1103;&#1073;.  3 16:01 initrd.img-3.16.0-24-generic
-rw-r--r-- 1 root root   176500 &#1084;&#1072;&#1088;&#1090;&#1072; 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 &#1084;&#1072;&#1088;&#1090;&#1072; 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 &#1084;&#1072;&#1088;&#1090;&#1072; 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  2109871 &#1089;&#1077;&#1085;&#1090;.  6  2012 System.map-2.6.38-16-generic
-rw------- 1 root root  2107662 &#1072;&#1087;&#1088;.  11  2011 System.map-2.6.38-8-generic
-rw------- 1 root root  3498860 &#1086;&#1082;&#1090;.  28 16:47 System.map-3.16.0-24-generic
-rw------- 1 root root     1217 &#1089;&#1077;&#1085;&#1090;.  6  2012 vmcoreinfo-2.6.38-16-generic
-rw------- 1 root root     1216 &#1072;&#1087;&#1088;.  11  2011 vmcoreinfo-2.6.38-8-generic
-rw------- 1 root root  4524112 &#1089;&#1077;&#1085;&#1090;.  6  2012 vmlinuz-2.6.38-16-generic
-rw-r--r-- 1 root root  4521296 &#1072;&#1087;&#1088;.  11  2011 vmlinuz-2.6.38-8-generic
-rw------- 1 root root  6401088 &#1086;&#1082;&#1090;.  28 16:47 vmlinuz-3.16.0-24-generic
i1@i1-GA-MA785GM-US2H:~$ grep vmlinuz /boot/grub/grub.cfg
   linux   /boot/vmlinuz-3.16.0-24-generic root=UUID=bf7ef48c-2fe3-4ec1-88b5-3ebe7de48121 ro  quiet splash $vt_handoff
      linux   /boot/vmlinuz-3.16.0-24-generic root=UUID=bf7ef48c-2fe3-4ec1-88b5-3ebe7de48121 ro  quiet splash $vt_handoff
      linux   /boot/vmlinuz-3.16.0-24-generic root=UUID=bf7ef48c-2fe3-4ec1-88b5-3ebe7de48121 ro recovery nomodeset 
      linux   /boot/vmlinuz-2.6.38-16-generic root=UUID=bf7ef48c-2fe3-4ec1-88b5-3ebe7de48121 ro  quiet splash $vt_handoff
      linux   /boot/vmlinuz-2.6.38-16-generic root=UUID=bf7ef48c-2fe3-4ec1-88b5-3ebe7de48121 ro recovery nomodeset 
      linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=bf7ef48c-2fe3-4ec1-88b5-3ebe7de48121 ro  quiet splash $vt_handoff
      linux   /boot/vmlinuz-2.6.38-8-generic root=UUID=bf7ef48c-2fe3-4ec1-88b5-3ebe7de48121 ro recovery nomodeset
```

grep linux-image | grep ^i...
```
natha@natha-GA-MA785GM-US2H:~$ dpkg -l | grep linux-image | grep ^i
ii   linux-image-3.16.0-24-generic                        3.16.0-24.32                              amd64        Linux kernel image for version 3.16.0  on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-24-generic                   3.16.0-24.32                             amd64        Linux  kernel extra modules for version 3.16.0 on 64 bit x86 SMP
natha@natha-GA-MA785GM-US2H:~$
```

How to remove nonexising images from grub menu configuration?

---

### Post by oldfred on 2014-11-10
They exist, just probably not in dpkg as you did an upgrade or over install without reformatting.
So files are still in /boot, but not registered.

If not in synaptic to delete you have to manually delete them. And that may just copy them into root's trash and you have to delete from there which can be a bit. I had some files in root's trash that I could not see even with sudo and had to temporarily change ownership of just root's trash folder. I immediately changed ownership of root's trash back to root so I did not screw up system.

 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a

If they are in database they should be here:

 In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

The command line way to purge also assumes that dpkg or apt-get purge has the kernels in the database. 

 [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

But probably not, so then you have to manually delete. The purge command deletes not just the vmlinuz, but all the other files with the same version number. So be sure to delete them also.

I would first try, if you have to manually delete.
gksudo nautilus

---

### Post by i12 on 2014-11-13
in \boot I see small files from old images, but all my filesystem is big -8 Gb for empty Ubuntu. rmkernel procedure works but changes nothing, synaptic see no old images.

---

### Post by coffeecat on 2014-11-13
Support thread.

*Thread moved to **General Help**.*

---

### Post by i12 on 2014-11-14
I deleted visible files manualy. Ubuntu takes 6,5 Gb space. Is it adequate for empty system with gnome+unity?

---

