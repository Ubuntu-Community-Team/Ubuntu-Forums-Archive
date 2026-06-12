---
title: "RAID 5 array wont resync"
date: 2006-10-29
forum: General Help
---

### Post by sphegdave on 2006-10-29
I updated to edgy from dapper and I made the mistake of letting the installation write its MBR to one of my drives in a software raid5 array. I figured no big deal, thats what raid is made for (ok not exactly but you get my drift). Anyways, I booted up the EVMS gui to check out the status of my array and add back in the drive. When I first did this, it displayed the message:

MDRaid5RegMgr : Region md/md0 is currently in degraded mode. To bring it back to normal state, add 1 new spare device to replace the faulty or missing device. 

I went ahead and deleted all the segments on the drive and then applied the changes. It seemed to automatically add the disk to the array and it seemed fine except that the array didn't seem to be resyncing. Restarting EVMS gave me this error:

MDRaid5RegMgr : Region md/md0 is currently in degraded mode. To bring it back to normal state, add 0 new spare device to replace the faulty or missing device. 

I cannot figure this out at all. If someone would like to give me some insight on this issue I would be much obliged.

Thanks!

---

### Post by sphegdave on 2006-10-30
Any takers?

---

