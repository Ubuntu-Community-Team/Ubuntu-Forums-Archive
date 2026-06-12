---
title: "Partiton recovery"
date: 2014-12-20
forum: General Help
---

### Post by medyas on 2014-12-20
hi all ,i was trying to fix my booting problem and i used testdisk but it cased the unallocated   all of my partition ,and i tried tesdisk again to fix it but i only managed to recover only 1 partition so can you help ?? and thnx.(didnt try deep scan )

[[IMG]http://s17.postimg.org/59jatio2z/image.jpg[/IMG]]("http://postimg.org/image/59jatio2z/")[http://postimg.org/image/59jatio2z/](http://postimg.org/image/59jatio2z/)

sudo fdisk -l

Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd2137754

Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1       316014678  693333269 377318592 179.9G  7 HPFS/NTFS/exFAT
/dev/sda2       693333333  737287109  43953777    21G  7 HPFS/NTFS/exFAT
/dev/sda3       737287110 1465144064 727856955 347.1G  f W95 Ext'd (LBA)
/dev/sda5       737287173 1465144064 727856892 347.1G  7 HPFS/NTFS/exFAT

Partition 2 does not start on physical sector boundary.

Partition 3 does not start on physical sector boundary.

Partition 4 does not start on physical sector boundary.

Partition 6 does not start on physical sector boundary.

---

### Post by deadflowr on 2014-12-20
What booting problems are you having?
This seems to be Windows related, as you only have partitions for Windows listed.
Is this Windows boot problem?

---

### Post by medyas on 2014-12-21
when i start my pc it say no partition to boot from ,so how do i get my partitions back ?? and sda3 is a copy of sda5 how to remove it .

---

### Post by medyas on 2014-12-21
[[img]http://s22.postimg.org/i02vkhb4d/image.jpg[/img]](http://postimg.org/image/i02vkhb4d/)

---

### Post by westie457 on 2014-12-21
You really ought to run the deep scan option to find the missing partitions. The quick search option only sees the current partition layout.

Post a screen shot of testdisk after the deeper search. It will take a long time.

---

### Post by Mark Phelps on 2014-12-21
> hi all ,i was trying to fix my booting problem and i used testdisk

It looks like all your partitions are/were NTFS -- and in that case, you would not be able to fix a boot problem the traditional way because Ubuntu only installs into an NTFS partition using WUBI -- and that does not use GRUB for booting.

Need to tell us more about the problem you are trying to fix and how you installed Ubuntu.

---

