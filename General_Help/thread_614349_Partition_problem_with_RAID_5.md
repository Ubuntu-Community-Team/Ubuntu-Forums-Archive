---
title: "Partition problem with RAID 5"
date: 2007-11-15
forum: General Help
---

### Post by htakai on 2007-11-15
I am installing Ubuntu 7.10 64 bits on a server with 7 TB of disk, RAID 5. The initial installation goes well and when we first mount the disk we can see the entire 7 TB.   When we go ahead and reboot the server, this partition (/dev/sdb1) has no longer 7 TB of disk, instead it goes down to 768 GB. 

I looked in /proc/partitiontable before and after the boot and the partition size for /dev/sdb1 has **magically**  changed!  Has anybody seen anything like this? What is the work around?

---

