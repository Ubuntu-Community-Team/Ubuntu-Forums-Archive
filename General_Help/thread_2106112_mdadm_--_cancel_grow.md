---
title: "mdadm -- cancel grow"
date: 2013-01-18
forum: General Help
---

### Post by lotharz0r on 2013-01-18
Hi.
I had 10 hard drives in raid 6 with one spare.
Now I have added 3 more drives, end started growing to 14 active devices.
One drive failed during the reshape, so the state of the array is now RESYNC=PENDING
> personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10]
md0 : active raid6 sdg1[5] sdf1[4] sdi1[6] sdb1[1] sdc1[0] sdd1[2] sdh1[7] sde1[3] sdk1[13] sdo1[14](F) sdm1[10] sdl1[11] sdn1[15] sdj1[12]
      15627055104 blocks super 1.2 level 6, 512k chunk, algorithm 2 [14/14] [UUUUUUUUUUU_UU]
        resync=PENDING


I have tried googling around a bit, but can't find out if I can cancel the grow operation, and go back to the 10 drive raid?

I just want to go back to the 10 drive raid until I get my replacement hard drive.

Anyone know if that is possible?

---

