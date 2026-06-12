---
title: "How to make swap partition permanent?"
date: 2007-06-11
forum: General Help
---

### Post by keithk50 on 2007-06-11
Recently upgraded my laptop HD after cloning my old one.   The cloning process worked really well and now I have more HD space for Ubuntu once I take it from the NFTS partition.   One small problem.   Each time I boot into Ubuntu I have to enable the swap via Gparted (right click on Ext3 partition and click 'swapon'.   No big deal really but it would be nice to have the swap enabled on login.   Swap was automaticly activated on the old HD.
The swap is shown here:

keith@keith-laptop:~$ fdisk -l
keith@keith-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         493     3959991   83  Linux
/dev/sda2   *         494        5534    40491832+   7  HPFS/NTFS
/dev/sda3            5535        7216    13510665   83  Linux
/dev/sda4            7217        7296      642600    5  Extended
/dev/sda5            7217        7296      642568+  82  Linux swap / Solaris
keith@keith-laptop:~$ 

Any help would be appreciated.   Please be gentle, I am still learning

---

### Post by taurus on 2007-06-11
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda5   none   swap   sw   0   0
```
Save it and reboot.

---

### Post by keithk50 on 2007-06-11
That worked a treat.   Thanks very much for your quick responce.   Learning all the time.:D

---

