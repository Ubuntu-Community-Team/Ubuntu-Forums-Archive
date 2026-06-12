---
title: "Kernel Panic - Not syncing"
date: 2008-02-18
forum: General Help
---

### Post by manij on 2008-02-18
Hi,

Have been running 6.06 with nor problems for awhile. I started having freezing problems recently while playing RTCW. I had to do a hard reboot few times and now I have this error on startup

***kernel panic-not syncing: VFS: unable to mount root fs on unknown-block (0,0)***


I read that this is a grub/menu.lst problem. 

[B][I]
I booted with a live CD and here is the info from fstab, menu.lst and fdisk -l from my main installation.
sdb1 is my linux install


FDISK -l

[B][I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       38913   312568641    b  W95 FAT32

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           5       14179   113860687+   7  HPFS/NTFS
/dev/sda2           14180       19452    42355372+   b  W95 FAT32

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14409   115740261   83  Linux
/dev/sdb2           14410       14593     1477980    5  Extended
/dev/sdb5           14410       14593     1477948+  82  Linux swap / Solaris[/I][/B]

MENU.LST

[B][I]title        Ubuntu, kernel 2.6.15-51-386
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro quiet splash
savedefault
boot

title        Ubuntu, kernel 2.6.15-51-386 (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-51-386 root=/dev/sdb1 ro single
boot

title        Ubuntu, kernel 2.6.15-29-386
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-29-386 root=/dev/sdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-29-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-29-386 root=/dev/sdb1 ro single
initrd        /boot/initrd.img-2.6.15-29-386
boot

title        Ubuntu, kernel 2.6.15-26-386
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1[/I][/B]

FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1     /home/manij/Desktop/winntfs ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/hdb1       /home/manij/Desktop/TIVODRIVE   vfat   iocharset=utf8,umask=000 0 0
/dev/sda2       /home/manij/Desktop/NTFS_FAT32   vfat   iocharset=utf8,umask=000 0 0[/I][/B]


I have read that this can be fixed by editing the menu.lst or fstab

how do I do this? Help!

---

### Post by manij on 2008-02-18
Little bit more info.

Here is the /boot list from my installation

[B][I]   4 drwxr-xr-x  3 root root    4096 2008-02-18 07:18 .
   4 drwxr-xr-x 21 root root    4096 2008-01-01 07:26 ..
 268 -rw-r--r--  1 root root  266735 2006-09-08 21:51 abi-2.6.15-26-386
 268 -rw-r--r--  1 root root  266735 2007-09-24 17:58 abi-2.6.15-29-386
 268 -rw-r--r--  1 root root  266735 2008-02-12 17:32 abi-2.6.15-51-386
  76 -rw-r--r--  1 root root   69978 2006-09-08 19:52 config-2.6.15-26-386
  76 -rw-r--r--  1 root root   69967 2007-09-24 17:17 config-2.6.15-29-386
  76 -rw-r--r--  1 root root   69967 2008-02-12 16:51 config-2.6.15-51-386
   4 drwxr-xr-x  2 root root    4096 2008-02-18 07:18 grub
6700 -rw-r--r--  1 root root 6846850 2008-01-01 07:26 initrd.img-2.6.15-26-386
6700 -rw-r--r--  1 root root 6847464 2008-01-01 07:26 initrd.img-2.6.15-29-386
 100 -rw-r--r--  1 root root   94760 2005-10-25 10:32 memtest86+.bin
 716 -rw-r--r--  1 root root  726461 2006-09-08 21:51 System.map-2.6.15-26-386
 716 -rw-r--r--  1 root root  727244 2007-09-24 17:58 System.map-2.6.15-29-386
 716 -rw-r--r--  1 root root  727244 2008-02-12 17:33 System.map-2.6.15-51-386
1388 -rw-r--r--  1 root root 1414735 2006-09-08 21:51 vmlinuz-2.6.15-26-386
1388 -rw-r--r--  1 root root 1415075 2007-09-24 17:58 vmlinuz-2.6.15-29-386
1388 -rw-r--r--  1 root root 1415019 2008-02-12 17:32 vmlinuz-2.6.15-51-386[/I][/B]

As you can see 

initrd.img--2.6.15-51-386 is missing. This the default kernel, i'm supposed to booot from

I recently did a upgrade and got the error message that it couldn't commit changes

is this creating prooblems?

HELP

My wife is ready to kill me!

mani

---

### Post by manij on 2008-02-18
I was able to boot of the one of the other kernels

My question is, how come the default or latest kernel image disappeared?

Mani:confused:

---

