---
title: "problem mounting dvr harddrive"
date: 2007-07-18
forum: General Help
---

### Post by Josey on 2007-07-18
I trying to mount a dvr harddrive.  I opened the dvr box and hooked up to the harddrive using a usb cable.  The device is recognized as /dev/sda/ 
I need to get files off here but Im getting this.

```
user@ubuntu:~$ fdisk -l

Disk /dev/sda: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

```

any ideas?

---

### Post by HermanAB on 2007-07-18
It doesn't seem to have a file system that Linux can recognize.  These things frequently use a 'raw' system in order to improve speed, so there probably is no file system, it just writes sectors.  You can copy the drive using 'dd' if that will help, but you probably won't ever be able to interpret the data.

---

### Post by Josey on 2007-07-21
After takling the hardware encryption on the hard drive I can get this, but I can only mount the first two partitions.  Anybody know how to mount the fourth partition?

```
user@ubuntu:~$ fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         244     1959898+  83  Linux
/dev/sda2             245         585     2739082+  83  Linux
/dev/sda3             586         613      224910   83  Linux
/dev/sda4             614       30401   239272110   83  Linux

```

---

### Post by Josey on 2007-07-21
This is what I get when I try to mount the fourth partition:

```
user@ubuntu:~$ sudo mount -t ext3 /dev/sda4 /media/dvr
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

