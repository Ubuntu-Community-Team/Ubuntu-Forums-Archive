---
title: "[SOLVED] Extra disk drives and partitions"
date: 2008-05-19
forum: General Help
---

### Post by dykesy61 on 2008-05-19
Hi
I have played with various flavours of Linux and settled on Ubuntu, due to the regular release schedule and support.

I have recently installed Hardy, having run Gutsy successfully for some time.
BUT, I now find that
a) my data partition is not automounted - it's sda3
b) when it mounts it mounts as hda3!
c) my extra disk drive also does not automount, and says its permissions are not obtainable.

any help to sort me out, please?
thanks

---

### Post by dykesy61 on 2008-06-13
Ok well I have got the extra partition to automount now.
but the extra drive with one partition now mounts but as "20.4 Gb Media".
I tried to get it to mount as "hdb1" which would make more sense to me!

here is my fdisk print out:

phil@phil-desktop:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001cdbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2            2551        2812     2104515   82  Linux swap / Solaris
/dev/sda3            2813        9964    57448440   83  Linux

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009b770

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2482    19936633+  83  Linux

---

### Post by dykesy61 on 2008-06-29
anyone out there?
any ideas?
thanks

---

### Post by vanadium on 2008-06-29
> Ok well I have got the extra partition to automount now.
Some people will be glad to know how you solved this. If you want help, do also provide help.

Since Hardy, volumes that do not have a label mount with a generic label such as "20.4 Gb Media". To mount it using a name of your choice, you have to give the partition a volume label.

---

### Post by dykesy61 on 2008-07-30
Thanks...I then labelled the drive using the partition editor, noting that the data would be lost (copied the files on it to my other drive), and then restarted linux.

Success...and much easier to see the drive now it is labelled as I wanted it to be.

Thanks for your help...sorry for the delay, I have just moved house!

---

