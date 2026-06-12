---
title: "Moving ubuntu to another drive."
date: 2008-05-15
forum: General Help
---

### Post by doctapeppa on 2008-05-15
Hello. I currently have ubuntu 8.04 on my /dev/sda drive. I have an identical drive on /dev/sdb and I would like to move my whole ubuntu onto the second drive so that I can install Vista on the first partition of the first drive. First I was thinking of copying everything over to the second drive but I figure I could just switch the SATA cables and achieve the same effect. I am worried, though, that I may break ubuntu this way; either way, actually. 

Is there a proper way to move Ubuntu to a different drive without breaking it?

here is the output of my fdisk -l 

```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ba2e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38157   306496071   83  Linux
/dev/sda2           38158       38913     6072570    5  Extended
/dev/sda5           38158       38913     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d088d08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       14594   117218304    7  HPFS/NTFS

```

---

