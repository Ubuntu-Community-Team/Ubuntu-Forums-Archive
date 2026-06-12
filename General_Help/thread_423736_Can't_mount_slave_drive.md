---
title: "Can't mount slave drive"
date: 2007-04-26
forum: General Help
---

### Post by Phieta on 2007-04-26
Hey there,

Just installed Feisty and am having trouble with my slave drive... fdisk -l returned this:
```

Disk /dev/hdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   ?           1        9730    78156193+   c  W95 FAT32 (LBA)
/dev/hdb2            9731       12161    19527007+   c  W95 FAT32 (LBA)
```

It shows that there are two FAT32 partitions there (which is correct), but I can't find a way to mount them... any suggestions? They work fine in Windows :\

Thanks!

---

### Post by Phieta on 2007-04-27
*bump*

Help, please? All I get is "mount: special device /dev/hdb1 does not exist" :\

---

### Post by Phieta on 2007-04-27
(bumping again, much as I don't want to)

Would it make a difference that the master drive (which works perfectly) was partitioned whilst installing Ubuntu, but the slave drive was partitioned ages ago with PartitionMagic in Windows?

---

### Post by ceno-byte on 2007-04-28
hello there Phieta im no linux expert im still a novice myself try following this guide i was having the same problem as you and this did the trick. wish you luck [http://www.smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux](http://www.smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux)

---

