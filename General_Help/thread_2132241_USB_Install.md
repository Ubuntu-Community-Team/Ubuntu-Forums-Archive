---
title: "USB Install"
date: 2013-04-04
forum: General Help
---

### Post by mld9373 on 2013-04-04
I am trying to read a usb thumb drive that has some files on it. i am have ubuntu 12.04 lts installed on my laptop. I have tryed to mount the drive to read the files with no luck. I also have wine installed. this thumb drive has some very imporant files on it that i need. does anyone have any i deals on how to read this read this thumb drive.

                                                                                                                                                                                                             thanks

---

### Post by ajgreeny on 2013-04-04
With the USB plugged in run the terminal command ```
sudo fdisk -l
``` (lower case L at the end) and let's see the output from that.

---

### Post by mld9373 on 2013-04-04
yo@yo-VGN-NS325J:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000acf86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   482379775   241188864   83  Linux
/dev/sda2       482381822   488396799     3007489    5  Extended
/dev/sda5       482381824   488396799     3007488   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 3079 MB, 3079667712 bytes
255 heads, 63 sectors/track, 374 cylinders, total 6014976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5841135b

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/sdc: 1027 MB, 1027604480 bytes
255 heads, 63 sectors/track, 124 cylinders, total 2007040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     2007039     1003488+   6  FAT16
yo@yo-VGN-NS325J:~$

---

### Post by Impavidus on 2013-04-04
/dev/sdc1 looks like the partition on your thumb drive. Can you check with```
mount
```whether it has been mounted on a less obvious place? Else try mounting it with```
mount /dev/sdc1 /your/mount/point
```Post any errors.

---

### Post by Slim Odds on 2013-04-04
> **Impavidus said:**
> /dev/sdc1 looks like the partition on your thumb drive. Can you check with```
mount
```whether it has been mounted on a less obvious place? Else try mounting it with```
mount /dev/sdc1 /your/mount/point
```Post any errors.

Use sudo, of course:
```
[COLOR=#a52a2a]sudo [/COLOR]mount /dev/sdc1 /your/mount/point
```

---

### Post by conradin on 2013-04-04
You might try installing testdisk.
also, if you can, use ddrescue to create an image, before attempting to do data-recovery.

---

