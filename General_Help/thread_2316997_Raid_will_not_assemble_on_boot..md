---
title: "Raid will not assemble on boot."
date: 2016-03-12
forum: General Help
---

### Post by PlugInPrius on 2016-03-12
I'm running Ubuntu 14.04

This may not be the best way to do things and if so let me know.

What I have is 2x 1.5TB drives and 3x 500GB drives.

I put the 3x 500GB drives into a raid 0. This gets assembled just fine as /dev/md126

I then made a raid 5 from my 2x 1.5TB drives plus md126. This gets named to md127

I was able to build it and mount it just fine for 3TB of redundant space.

After a reboot md126 will be assembled but md127 does not.

md126 : active raid0 sdf1[1] sdg1[2] sde1[0]
      1465153024 blocks super 1.2 512k chunks
      
md127 : inactive sdd1[1](S) sdc1[0](S)
      2930012160 blocks super 1.2


What I can do after a reboot is stop md127 then do a force assemble of sdc1 sdd1 and md126. Then mount it and I have my 3TB of storage back.


So what do I need to do to get this to assemble correctly at boot?

---

### Post by PlugInPrius on 2016-03-16
I found a few more 500gb drives and decided to go a different route. Raid 1 on the 1.5TB drives and raid 5 on 6 500gb drives. Then LVM on top of those.

---

