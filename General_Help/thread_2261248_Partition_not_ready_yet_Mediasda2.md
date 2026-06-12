---
title: "Partition not ready yet Media/sda2"
date: 2015-01-17
forum: General Help
---

### Post by dallase1 on 2015-01-17
Every time I boot up Linux I get a message on the booting screen Media/sda2 is not ready yet or not present hit S to skip or M to manually mount
This is the partition that has Windows 7 installed on it and it is a NTFS file system. This problem started happening after I had to reinstall Windows 7 because of viruses and Malware. I did not change the order or size of any of the partitions, all I did was delete the partition and then recreate it with Gparted and then reinstalled Windows 7 The Partition is not corupt and can be accesed from the file manager in Linux and is shown in the Computer Window that lists all the mounted and un mounted drives and / or partitions. How do I tell Linux to not try to mount that partition during boot up so I don't have to wait around to hit S to teel it to skip trying to access that partition?

---

### Post by Holger_Gehrke on 2015-01-17
Since you deleted and re-created the windows partition,it's UUID has probably changed. If the old UUID is still in '/etc/fstab' ...

Take a look at the output of 'sudo blkid' and at the file '/etc/fstab'

---

### Post by dallase1 on 2015-01-17
Fixed it I edited the FSTAB file to make the UUID for dev/sda2 to match the output of the sudo blkid command and now it boots up without me having to wait to hit S to have it skip trying to mount the partition.

---

