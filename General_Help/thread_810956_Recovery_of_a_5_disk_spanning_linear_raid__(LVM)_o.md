---
title: "Recovery of a 5 disk spanning linear raid  (LVM) on Ubuntu 7.1"
date: 2008-05-28
forum: General Help
---

### Post by diagpope on 2008-05-28
Hardware:
System P4 x2 Ubuntu 7.1 server, 5 disks (1 ATA)
sdb 300GB SATA Maxtor (died)
 sdb1 4.8 GB /
 sdb3 1..2GB swap
 sdb2 remaining space as first device of LVM

sdc1 120 GB Maxtor SATA part of LVM
sda1 250 GB WD SATA part of LVM
sdd1 250 GB WD SATA part of LVM
sde1 250 GB WD ATA  part of LVM


Problem: sdb1 died and the partition table got damaged
Actions: 
- Regenerated part table (no backup), used gpart
- gpart did not find the swap partition 
   => no idea where the LVM for sdb2 starts and ends
- rescued the /etc dir to an external disk

The LVM was --raid-level=linear

Status: 
	The sdb disk is still broken (seek failure) but boots the system

Question: 
	Can I scan for the start and end of sdb2, maybe the superblock and/or its copies since dd on sdb2 fails with seek errors?
        Are there superblocks on the remaining 4 drives I can scan for, how?
	Can I read / recover at least the data residing on the 4 drives?
Thanks for any commment

---

