---
title: "Dapper 6.06.1 RAID-1 disk failure crashes kernel"
date: 2006-10-25
forum: General Help
---

### Post by Frank-Hamersley on 2006-10-25
OK - we are now 2 for 2 ... a single disk failure on a RAID-1 configured Dapper Server 6.06.1 seems capable of bringing the server down!

I have a pair of Seagate ST3160812A 160G drives mirrored and have now had 2 catastrophic disk failures plus several hiccups (overcome by a cold start) in the last 4 months.  These events are not expected (by me at least) to be a problem - disks are under warranty and RAID-1 is deployed! The system will chug on regardless...won't it!

Wrong - it chokes!  The keyboard interrupt is still alive as you can <Alt><F2> to another console, even see the user name echoed back...but thats all.

Unplug the offending disk and away we go.  I have seen md take disks offline in RH7.3 without causing a system down but in those cases I don't think they were truly faulty as simply re-adding them to the array cleared the problem.  I suspect they were manifestations of driver stuff ups rather than a real HW event.

Am I expecting too much? Is there a latent problem in 2.6 etc? In fact should this be buzilla'ed to the kernel mob?

Regards, Frank.

---

