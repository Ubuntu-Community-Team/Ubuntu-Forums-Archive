---
title: "General Raid Opinion"
date: 2007-02-27
forum: General Help
---

### Post by scottsanpedro on 2007-02-27
Hi,
I have 4 SCSI hard drives,
3 x 73gb
1 x 36gb

Spent the evening trying to figure out a good raid configuration.
Tried Raid5 with 4 partitions and got GRUB errors.
I assume GRUB doesn;t run on Raid5

Was now thinking of two raid1 mirrored drives, 2 x 73gb and 2 x 36gb

Anyone have any thoughts on this or see any pitfalls? Thanks Scott

---

### Post by scottsanpedro on 2007-02-27
also..what about mirroring the swap, any reason not to? cheers

---

### Post by uiteoi on 2007-03-06
I have a similar configuration.

Assuming sdd is 36GB, to make the best use of all drives partition as follows:
- 200 MB /boot ext3 on md0 RAID1 (nothing else or GRUB and LILO will fail) on sda sdb sdc
- 1 GB swap on md1 RAID5 on sda sdb sdc => 2 GB swap
- 35.8 GB lvm on md2 RAID5 on sda sdb sdc => 72 GB
- 36 GB lvm on md2 RAID5 on sda sdb sdc sdd => 108 GB

Combine the 2 lvm partitions to build a 180 GB volume that you can then either use directly as / or split between resizeable partitions, Use ReiserFS if you want to be able to resize easily.

Instead of lvm, you could also use the last 2 partitions as ext3 but with less flexibility.

---

