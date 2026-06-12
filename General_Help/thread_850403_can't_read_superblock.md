---
title: "can't read superblock"
date: 2008-07-05
forum: General Help
---

### Post by FXEF on 2008-07-05
When I try to mount a 2GB SD media card I get this error "can't read superblock".

Here is fdisk -l and mount output:

Disk /dev/sdf: 2059 MB, 2059403264 bytes
38 heads, 37 sectors/track, 1430 cylinders
Units = cylinders of 1406 * 1024 = 1439744 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        2861     4022029    6  FAT16

bob@bob-desktop:~$ sudo mount -t FAT16 /dev/sdf1 /mnt/cwin
mount: unknown filesystem type 'FAT16'
mount: maybe you meant 'vfat'?
bob@bob-desktop:~$ sudo mount -t vfat /dev/sdf1 /mnt/cwin
mount: /dev/sdf1: can't read superblock

I also get the same "can't read superblock" message when F-Spot tries to mount this volume.

I am using a USB multicard reader that works fine with a 256MB Compact Flash card.

---

### Post by HalPomeranz on 2008-07-06
Have you tried mounting this same SD card on some other system?  Maybe even a Windows box or a Mac if you have one lying around.  It's possible that it's a problem with the SD card itself.

---

### Post by FXEF on 2008-07-06
> **HalPomeranz said:**
> Have you tried mounting this same SD card on some other system?  Maybe even a Windows box or a Mac if you have one lying around.  It's possible that it's a problem with the SD card itself.

This SD card in the USB card reader will not mount on a Vista box, however the same SD card will mount OK using the internal card reader on the Vista box.

Must be a USB card reader issue, not reading the SD card. :guitar:

---

