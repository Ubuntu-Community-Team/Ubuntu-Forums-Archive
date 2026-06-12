---
title: "Unable to mount NTFS USB drive"
date: 2008-04-17
forum: General Help
---

### Post by timboellis on 2008-04-17
I am running Kubuntu 8 and unable to mount well open my NTFS USB drive

When i open dolphin i see the drive as sda1 but when i click on it i get

mount@ wrong fs type, bad superblock on /dev/sda1, missing codepage or helpdes program


[PHP]tim@Timbo:~$ sudo sfdisk -l

Disk /dev/hda: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+  19081   19082- 153276133+  83  Linux
/dev/hda2      19082   19456     375    3012187+   5  Extended
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5      19082+  19456     375-   3012156   82  Linux swap / Solaris

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  60800   60801- 488384001    7  HPFS/NTFS
/dev/sda2          0       -       0          0    0  Empty
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty
[/PHP]

---

### Post by wdaniels on 2008-04-17
Maybe there's something wrong in /etc/fstab, can you post that file also?

---

### Post by timboellis on 2008-04-17
thanks for the response but what I have decided to do an am doing now is trasfering all my data from that drive to anothe rone in windows and then i will format it to fat32 that should fix the issue

---

