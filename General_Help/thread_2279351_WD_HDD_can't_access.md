---
title: "WD HDD can't access"
date: 2015-05-22
forum: General Help
---

### Post by iamtuggle on 2015-05-22
i'm running 15.04. it recognizes my external but i can't access it.  i have looked everywhere for a solution.  help please

---

### Post by sandyd on 2015-05-22
Moved to *General Help*

Can you post the output of```
 sudo fdisk -l
```

---

### Post by iamtuggle on 2015-05-23
Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C45105C1-1C93-4FCF-97E5-737F90B5A32F

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1050623    1048576   512M EFI System
/dev/sda2     1050624 1456957439 1455906816 694.2G Linux filesystem
/dev/sda3  1456957440 1465147391    8189952   3.9G Linux swap

Disk /dev/sdb: 14.9 GiB, 15931539456 bytes, 31116288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdd21f046

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1        2048 31116287 31114240 14.9G 83 Linux

---

### Post by Vladlenin5000 on 2015-05-23
In your thread's title you mention "HDD" and in the OP you mention "it recognizes my external but i can't access it"...
However, your fdisk results show two drives:
sda -> your system drive with the expected partitions for a standard EFI installation and *presumably* Ubuntu as your only OS
sdb -> A 16GB USB flash drive, perhaps?

Are you referring to sdb? If so and considering it has a Linux file system then probably it's a permissions issue.
Please confirm whether or not this is the "WD HDD" you're referring to... Unlikely, but if other then it ISN'T being recognized.

---

