---
title: "grub install"
date: 2007-01-03
forum: General Help
---

### Post by ESPOiG on 2007-01-03
im trying to install grub so...

su
grub-install /dev/sdc

but i keep getting the error "Could not find device for /boot: Not found or not a block device."
and i tryed sdc2 and sdc3, anyway here is my fdsik -l

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17652   141789658+   7  HPFS/NTFS
/dev/sda2           17653       30400   102398310    f  W95 Ext'd (LBA)
/dev/sda5           17653       30400   102398278+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       25064   201318547+   f  W95 Ext'd (LBA)
/dev/sdb5               2       25064   201318516    b  W95 FAT32

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           29749       30401     5245222+  82  Linux swap / Solaris
/dev/sdc2               1        7556    60693538+  83  Linux
/dev/sdc3            7557       29748   178257240   83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdd5               2       24321   195350368+   7  HPFS/NTFS

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       24321   195358401    7  HPFS/NTFS


---

### Post by Sef on 2007-01-03
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by ESPOiG on 2007-01-04
thats not what i wanna do, im trying to install gfx grub but last time i had to install grub before gfx would work?? now it doesnt want to install it at all :S

---

