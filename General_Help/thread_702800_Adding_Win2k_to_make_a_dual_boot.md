---
title: "Adding Win2k to make a dual boot"
date: 2008-02-20
forum: General Help
---

### Post by Robbyx on 2008-02-20
Most of the time I use Ubuntu but  a few programs must be run under windows. 

I have been using Vmware player and/ or server but I am finding it too difficult to work out how to make the virtual drive larger. I am therefore proposing to install win2k on a spare disk ie hda. 

I can not get the installation to start because the CD reports that hda2 does not contain a win 2 compatible partition. I have used gparted to put on a fat32, that did not allow the installation of win2k. 

I have tried deleting the contents of the partition as part of the win 2k installation and then formating it under the installation disk but it also rejects it and says that the partition is not win2 compatible. I do not have  a win98 repair disk. What should I do to have the right form of partition? It is important that I get this Win2k installation going ahead.

```
sudo fdisk -l
[sudo] password for robin:

Disk /dev/sda: 250.0 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02470247

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        5051       14593    76654147+  83  Linux
/dev/hda2               1        5050    40564093+   e  W95 FAT16 (LBA)

Partition table entries are not in disk order

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e433e42

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391    b  W95 FAT32
/dev/hdb2              14         268     2048287+  83  Linux
/dev/hdb3             269        2169    15269782+  83  Linux
/dev/hdb4            2170        5005    22780170    f  W95 Ext'd (LBA)
/dev/hdb5            3700        4591     7164958+   7  HPFS/NTFS
/dev/hdb6            2170        3699    12289662    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdd: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf55bf55b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2493    20024991   83  Linux
/dev/hdd2            4796        5005     1686825    5  Extended
/dev/hdd3            2494        4795    18490815   83  Linux
/dev/hdd5            4796        5005     1686793+  82  Linux swap / Solaris

Partition table entries are not in disk order
robin@robin-desktop:~$ 

```

---

### Post by zvacet on 2008-02-20
> I am finding it too difficult to work out how to make the virtual drive larger

That is because vmware-server is installed in /var/lib meaning in your root.I belive you have larger home and you can install it there.Reading [this](http://ubuntuforums.org/showthread.php?t=491852&highlight=vmware+server+install) may point you to the direction you want to go.

---

