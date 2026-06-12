---
title: "Raid drive upgrade setup"
date: 2007-10-22
forum: General Help
---

### Post by IcarusR on 2007-10-22
Hi
I have a 3ware 8005 2 port raid card with 2 320 Gb drives in raid1. These drives are no longer big enough. I have two new drives. 
If I plug new drives into mobo SATA ports, partition, format & rsync from old drives on 8005 when I install new drives on the 8005 will it just setup raid without affecting the data. 
Or am I better off installing the new drives on the 8005 & old drives on the mobo then partitioning, formatting & rsyncing the new drives.

In short what is the best, most efficient way to setup these new drives on my 8005 without loosing any data.

Thanks Icarus

---

### Post by thirddeep on 2007-10-22
First -and always- backup your data.  Now, I don't know the 8005 and it's capabilities, but this in theory should work if you have already LVM running on that partition:

1) Pull 1 old drive
2) Put 1 new big drive in
3) Rebuild array
4) Pull last old drive
5) Put second new big drive in
6) Rebuild array
7) Expand array to fill HDD
8) Expand LVM Group
9) Expand LVM Volume
10) Expand File system

If the above fails, you still have your data and can build a new array -with LVM- on the 2 large shiny HDD's

Thd.

---

### Post by IcarusR on 2007-10-22
thirddeep thanks for your reply.
I do not have LVM installed. I don't know if I install it now & it will work ?? Will have to read about LVM.
The origional drives are partitioned down to 3 partitions. The new ones will be 3 of similar size & an extra one using the remaining space. 
Origional partitions are formatted ext3 but the new 4th one will be xfs. Don't know if this makes any difference.

Icarus

---

### Post by IcarusR on 2007-10-23
Got it sorted. Just installed 2 new drives, built array, partitioned & did a rsync of a backup.
Working well now.

Icarus

---

