---
title: "Help Formating ppc hd"
date: 2008-03-27
forum: General Help
---

### Post by OneSub on 2008-03-27
I resently tried to install gentoo on an ibook g4, but during reboot ... yaboot came up saying  invalid or corrupt,..    
I rebooted the ibook and pressed ctrl+c to boot from cd,.. it would not boot from a cd, (I tried many times with different disks)

so... I pulled the hd and connected it to another laptop(ubuntu) via usb

I ran the fallowing commands:

```

tybalt@mechasun:~$ mkfs.ext3 /media/disk
mke2fs 1.40.2 (12-Jul-2007)
/media/disk is not a block special device.
Proceed anyway? (y,n) y
mkfs.ext3: Device size reported to be zero.  Invalid partition specified, or
        partition table wasn't reread after running fdisk, due to
        a modified partition being busy and in use.  You may need to reboot
        to re-read your partition table.

tybalt@mechasun:~$ cd /media/disk
tybalt@mechasun:/media/disk$ dir
bin   etc           iface       mnt   root                       sys  var
boot  hardware.txt  lib         opt   sbin                       tmp
dev   home          lost+found  proc  stage1-ppc-2007.0.tar.bz2  usr
tybalt@mechasun:/media/disk$ ls -l
total 29588
drwxr-xr-x  2 root root     4096 2008-03-26 22:13 bin
drwxr-xr-x  2 root root     4096 2007-04-22 15:02 boot
drwxr-xr-x  5 root root    36864 2008-03-25 01:50 dev
drwxr-xr-x 24 root root     4096 2008-03-27 08:30 etc
-rw-r--r--  1 root root        0 2008-03-27 08:03 hardware.txt
drwxr-xr-x  2 root root     4096 2007-04-22 15:02 home
-rw-r--r--  1 root root        4 2008-03-25 01:50 iface
drwxr-xr-x  4 root root     4096 2008-03-26 22:16 lib
drwx------  2 root root    16384 1904-01-04 18:13 lost+found
drwxr-xr-x  4 root root     4096 2007-04-22 15:02 mnt
drwxr-xr-x  2 root root     4096 2007-04-22 15:02 opt
drwxr-xr-x  2 root root     4096 2007-04-22 14:59 proc
drwx------  2 root root     4096 2008-03-25 11:32 root
drwxr-xr-x  2 root root     4096 2008-03-26 22:16 sbin
-rw-r--r--  1 root root 30144379 1904-01-04 18:18 stage1-ppc-2007.0.tar.bz2
drwxr-xr-x  2 root root     4096 2007-04-22 15:02 sys
drwxrwxrwt  2 root root     4096 2008-03-27 08:08 tmp
drwxr-xr-x 12 root root     4096 2008-03-25 01:57 usr
drwxr-xr-x 12 root root     4096 2008-03-25 11:34 var
tybalt@mechasun:/media/disk$ sudo mac-fdisk /media/disk
[sudo] password for tybalt:
sudo: mac-fdisk: command not found
tybalt@mechasun:/media/disk$ 
```

i tried to see if I had mac-fdisk there at the end,...  :/


,....  so some help deleting all my files boys??  (and girls)

---

### Post by pointone on 2008-03-27
Don't refer to /media/disk (the mountpoint), refer to the device itself, which should be "/dev/sd*", where * is a, b, c, etc.

```
cat /etc/mtab | grep /media/disk
```

... will allow you to find out the correct device.

---

### Post by OneSub on 2008-03-27
Thanks! 

works Great!

---

