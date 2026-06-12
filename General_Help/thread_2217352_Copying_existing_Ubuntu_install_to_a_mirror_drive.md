---
title: "Copying existing Ubuntu install to a mirror drive"
date: 2014-04-16
forum: General Help
---

### Post by canonjimmy42 on 2014-04-16
I have my current, working, happy 12.04LTS install on /dev/sda, a 1TB drive.  I have an identical model 1TB drive unused, as /dev/sdb.  Can I boot from a live CD and do a "dd if=/dev/sda of=/dev/sdb bs=4096", go to bed, wake up, and have 2 bootable, identical disks?

More to the point, I'm wanting to RAID-1 mirror these.  When I set them as RAID-1 mirror in my controller, will it nuke the contents of the drives?

I'm just stumped, and without external backup options other than the two 1TB disks.

The only posts I am finding on this subject are from 2004, so I'm a little hesitant to start doling out commands at a root prompt from 10 years ago.

Thanks so much for any responses!

---

### Post by ian-weisser on 2014-04-16
Usually the raid controllers I have used do the mirroring. So all your dd work will get nuked.

---

