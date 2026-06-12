---
title: "GRUB help"
date: 2006-12-30
forum: General Help
---

### Post by gitargr8 on 2006-12-30
Hello all, I just installed Ubuntu 6.10, and everything went fine, but I installed grub to the wrong boot partition. I have two hard drives, a 320 GB SATA drive that I want to boot off of, and a 120 GB IDE drive that grub was installed to.

The way I see it, I have three options:

  1) change the Windows boot.ini to include Ubuntu

  2) install GRUB to the correct MBR

  3) reinstall Ubuntu

Obviously the easiest for me would be number 3, but that is time consuming and would much prefer 1 or 2. If anyone can help, I would greatly appreciate it.

~Ryan

---

### Post by bulldog on 2006-12-30
On which disk is ubuntu?
Can you give me the output of
```
sudo fdisk -l (l as in like)
cat /boot/grub/device.map
```

---

### Post by gitargr8 on 2006-12-30
Sure thing:
```

root@ryan-desktop:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528       38912   260132512+   f  W95 Ext'd (LBA)
/dev/sda5            6528       37607   249650068+   7  HPFS/NTFS
/dev/sda6           37608       38912    10482381   83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/hdb2            3917       14592    85754970    f  W95 Ext'd (LBA)
/dev/hdb5            3917       14592    85754938+   7  HPFS/NTFS
root@ryan-desktop:~# cat /boot/grub/device.map
(hd0)   /dev/hdb
(hd1)   /dev/sda


```

---

### Post by bulldog on 2006-12-30
You don't have a swap partition?
It seems your linux partition is on sda so you have to install GRUB on (hd1)

Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd1)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by gitargr8 on 2006-12-31
Sorry for asking dumb questions, but will this be able to detect the windows installation and boot to it as well?

---

### Post by bulldog on 2006-12-31
It should but even if it isn't you can add it manually, a one minute job.

---

