---
title: "RAID recovery from failed array...."
date: 2014-09-19
forum: General Help
---

### Post by Shawn67 on 2014-09-19
I have a system with 4 physical drives. Each drive has two partions (1 in a Raid 5 software array. The is a md0  and md1 arrays configured across those four drives.

Looks like I had a drive fail (though it is still showing up in the bios) and to make things slightly more interesting it looks like additionally another of the partitions on MD0 also failed. This is preventing the system from booting.

mdadm for md0 is showing
State active, Failed, Not Started.
Active Devices 2, Working Devices 2. 

Numbers 0 and 2 are listed as removed. 1 and 3 are active sync. /dev/sdb1 , /dev/sdd1

mdadm for md1 is showing
State: clean, degraded
Active/Working devices 3
Number 0 is listed as removed and 1,4,3 are showing as active sync. /dev/sbd5, /dev/sdc5, /dev/sdd5


In the past I replaced a failed drive and repartioned it and added the partitions to the two arrays and they rebuilt themselves fine. In that case both raid arrays were active though.

Suggestions on best way to proceed to get md0 active? Right now the system is just booting into an initramfs.

Thanks,

Shawn

---

