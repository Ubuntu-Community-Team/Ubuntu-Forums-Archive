---
title: "unknown filesystem type 'LVM2_member'"
date: 2013-02-12
forum: General Help
---

### Post by tetard on 2013-02-12
Hello,
I am actually having similar problems that I can't resolve with the previous answers. On Ubuntu 10.04, I have a 3-Ware hardware RAID-5 with 4 disks. They altogether make a single 750GB volume which I can not mount anymore. Any suggestion how to mount this volume, or possibly test for potential problems (HD failure?) will be most welcome.

Here is some information on my system :

```

line in /etc/fstab :
UUID=ZwkUgu-ZHd0-6IkK-ebhn-fT3u-ik7Z-RruWam   d2   ext3 defaults   0 0

```

```

ls /dev/mapper
control

```

```

blkid /dev/sda2
/dev/sda2: UUID="ZwkUgu-ZHd0-6IkK-ebhn-fT3u-ik7Z-RruWam" TYPE="LVM2_member" 

```

```

sudo fdisk -l

Disk /dev/sda: 750.0 GB, 749966721024 bytes
255 heads, 63 sectors/track, 91178 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000edc62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26       91178   732186472+  8e  Linux LVM

```

Thanks in advance for your time and consideration

---

