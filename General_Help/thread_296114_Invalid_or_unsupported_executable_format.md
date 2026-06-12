---
title: "Invalid or unsupported executable format"
date: 2006-11-09
forum: General Help
---

### Post by mosestruong on 2006-11-09
I have dual boot on my laptop. Recently, I can no longer boot into Ubuntu. When I try, I get the following error:

Error 13: Invalid or unsupported format

My menu.lst for the Ubuntu section is as follows:

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,4)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

My fdisk -l output as follows:
Disk /dev/hda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1530    12284968+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            1530        7301    46360251+   f  W95 Ext'd (LBA)
/dev/hda5            1530        1543      105808+  83  Linux
/dev/hda6            1543        1674     1050808+  82  Linux swap / Solaris
/dev/hda7   *        1674        3586    15361888+  83  Linux
/dev/hda8            3969        7301    26772291   83  Linux
/dev/hda9            3587        3968     3068383+   b  W95 FAT32

Partition table entries are not in disk order

Are there any way this can be fixed? Thanks.

---

### Post by bbiwyou on 2006-11-09
Wrong file path perhaps ?

kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda7 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic


On ubuntu, kernel images are usually located under /boot

---

### Post by mosestruong on 2006-11-09
no - the path is correct - i have a separate boot partition...

what concerns me is the "Partition 1 does not end on cylinder boundary." message from fdisk - but I'm not sure if that has anything to do with it or whether that is a separate error I need to look into...

---

