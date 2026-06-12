---
title: "Recover/Mount an NTFS Fakeraid drive - assistance would be appreciated/ HELP!"
date: 2008-01-25
forum: General Help
---

### Post by PlatnumYoda on 2008-01-25
Hi everyone,  any assistance would be much appreciated!

I have checked other threads on this topic and none seem to be of much assistance.  My Windows PC melted down,  I think it was just the main drive (installed on a 60gig hard drive),  though I also had a 16gig drive and two 200gig drives which were/are setup in a raid 0 stripe under fakeraid.  I have installed ubuntu on the 16 gig drive and am trying to mount the Raid drive so that I can access/recover the contents.  I'm not 100% sure that the hardware failure did not also effect the RAID drive (see results of fdisk -l below.

I have also pasted results of dmraid -r and dmraid -tay if that is any use.  Not sure where to go from here as the primary howto seems to be on setting up a UBUNTU installation from scratch on a Fakeraid drive,  and as I understand it seems to involve formatting the drive which would defeat the purpose in terms of what I am looking to do.

Any guidance would be much appreciated.




joe@joe-desktop:~$ sudo dmraid -r
/dev/sda: sil, "sil_aeahdfaaagfc", stripe, ok, 390718848 sectors, data@ 0
/dev/sdb: sil, "sil_aeahdfaaagfc", stripe, ok, 390718848 sectors, data@ 0

joe@joe-desktop:~$ sudo dmraid -tay
[sudo] password for joe:
sil_aeahdfaaagfc: 0 781437696 striped 2 128 /dev/sda 0 /dev/sdb 0
sil_aeahdfaaagfc1: 0 781433667 linear /dev/mapper/sil_aeahdfaaagfc 63


joe@joe-desktop:~$ sudo fdisk -l

Disk /dev/hda: 15.3 GB, 15377080320 bytes
255 heads, 63 sectors/track, 1869 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d271d26

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1785    14337981   83  Linux
/dev/hda2            1786        1869      674730    5  Extended
/dev/hda5            1786        1869      674698+  82  Linux swap / Solaris

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70466764

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48642   390716833+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/dm-0: 400.0 GB, 400096100352 bytes
255 heads, 63 sectors/track, 48642 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70466764

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1               1       48642   390716833+   7  HPFS/NTFS

Disk /dev/dm-1: 400.0 GB, 400094037504 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by fjgaude on 2008-01-27
Have you tried mounting the raid0 array?

```
sudo mount -t ntfs /dev/mapper/sil_aeahdfaaagfc /raid
```

with the /raid being your made mount poiint.

```
sudo mkdir /raid
```

You can use any other mount point that you like.

---

### Post by PlatnumYoda on 2008-02-02
Thanks a million.  The below worked.

> joe@joe-desktop:~$ sudo mount -t ntfs /dev/mapper/sil_aeahdfaaagfc1 /raid


---

### Post by fjgaude on 2008-02-03
Wonderful! You can indicate the post as [SOLVED].

---

