---
title: "fdisk changing disk order every reboot"
date: 2008-05-13
forum: General Help
---

### Post by Keldek on 2008-05-13
I'm back again, with a more simplictic problem this time I hope.

My previous problem ended up leading to a fresh install with all my hardware connected before hand.

I've gotten things reinstalled fine, but now it seems like fdisk is toying with me...

first boot: 'sudo fdisk -l'
```
keldek@System-X:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48674866

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19         747     5855692+  83  Linux
/dev/sda3             748        1963     9767520   83  Linux
/dev/sda4            1964       30401   228428235    5  Extended
/dev/sda5            1964        2571     4883728+  83  Linux
/dev/sda6            2572       30401   223544443+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48b648b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244198583+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007d1cc

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4eb7c8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sde: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4eb7c8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdf: 253 MB, 253231104 bytes
16 heads, 32 sectors/track, 966 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x84e4327b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         965      247024    b  W95 FAT32

```

Upon reboot: 'sudo fdisk -l'
```
keldek@System-X:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4eb7c8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4eb7c8e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48674866

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          18      144553+  83  Linux
/dev/sdc2              19         747     5855692+  83  Linux
/dev/sdc3             748        1963     9767520   83  Linux
/dev/sdc4            1964       30401   228428235    5  Extended
/dev/sdc5            1964        2571     4883728+  83  Linux
/dev/sdc6            2572       30401   223544443+  83  Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48b648b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30402   244198583+   7  HPFS/NTFS

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007d1cc

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdf: 253 MB, 253231104 bytes
16 heads, 32 sectors/track, 966 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x84e4327b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         965      247024    b  W95 FAT32

```

Any thoughts on why the 2 300GB disks would keep going back and forth between /dev/sda & dev/sdb to /dev/sdd & /dev/sde ?

I would like to move past this, get my raid setup installed and finish setting up my system but I'm afraid to make any changes.

Any advice is very much appreciated.

My system:
Ubuntu 8.04 x86_64 (2.6.24-16-generic kernel)
MSI K9A2 Platinum (Promise raid controller disabled in BIOS due to driver issues in ubuntu)
3x 250GB SATA disks using onboard SATA controller operating in IDE mode
2x 300GB SATA disks on Silicon Image SIL3114 SATA controller

Thanks in advance.

---

### Post by ryanhaigh on 2008-05-13
Something was changed in the kernel/udev which means that disks may not always get the same designation, this is why an ubuntu install (since feisty I believe) will use UUIDs in your grub, fstab and initrd configurations. A little more information:

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://wiki.ubuntu.com/LibAtaForAtaDisks](https://wiki.ubuntu.com/LibAtaForAtaDisks)

I don't think you can stop the partitions changing the /dev/sd* but if you have the uuid for the partitions in fstab they should be mounted in their proper locations anyway.

---

### Post by Keldek on 2008-05-13
Thanks for the info, though I only need to update the entries in my /etc/crypttab file. but this will definitely help me sleep better at night :guitar:

---

### Post by fjgaude on 2008-05-14
It seems that Hardy doesn't change drive names. Another thing is that mdadm does use drive names but the superblocks to assemble an array. The /dev/md[nn] name is aways valid, from hardware setup to a new one. So you can sleep well.

With a new setup, just use assemble to get the array up and running again.

```
sudo --assemble --scan
```

That does it.

---

