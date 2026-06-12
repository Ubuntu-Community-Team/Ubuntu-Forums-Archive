---
title: "mounting second hard drive on boot"
date: 2008-04-15
forum: General Help
---

### Post by sciff90 on 2008-04-15
how do i automatically mount my second ext3 hard drive

getting annoying having to mount manually after every boot

Thanks any input will be appreciated

---

### Post by Tomatz on 2008-04-15
Post the output of this:

```
sudo fdisk -l
```

---

### Post by sciff90 on 2008-04-15
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5759972d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29650   238163593+  83  Linux
/dev/sda2           29651       30401     6032407+   f  W95 Ext'd (LBA)
/dev/sda5           29651       30401     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d199d19

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00009395

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9761847b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60802   488386568    7  HPFS/NTFS

Disk /dev/sde: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8d4adaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        2431    19526976    c  W95 FAT32 (LBA)

---

### Post by Tomatz on 2008-04-15
Lots of storage lol.

Which partition do you want to automaticly mount?

---

### Post by sciff90 on 2008-04-15
the hard drive i want to automatically mount is dev/sdb

---

### Post by Tomatz on 2008-04-15
Type this in a terminal:

```
sudo gedit /etc/fstab
```

Then in the file paste this at the bottom:

```
/dev/sdb       /media/sdb     ext3    defaults        0       2
```

**Save**

Then reboot ;)

---

### Post by sciff90 on 2008-04-15
worked great thanks

---

### Post by Tomatz on 2008-04-15
Great ;)

Glad to help.

---

