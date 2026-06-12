---
title: "RAID 1 test post mortem"
date: 2014-08-14
forum: General Help
---

### Post by john_m2 on 2014-08-14
Testing a software RAID 1 on Trusty (64 bit server build). Ended up with a total failure of both drives.

I created a RAID 1 as follows

/dev/md0 /dev/sda1 /dev/sdb1 /
/dev/md1 /dev/sda5 /dev/sdb5 swap

All working. Exercised it a bit installing packages and what not. Now to test a disk failure.

I shut down and removed sda, rebooted and all ok. Boots degraded just as expected. 

I then reformatted the disk I removed, removing all partitions. I then shut down box and reinstalled disk. Now you noticed I did not use mdadm to remove the failed drive and maybe that was the problem.

Upon starting up  it goes to the normal boot but then drops into a busybox when it tries to mount the fs. Looking back through the log messages it appears that it recognized the degraded state but assigned /dev/sdax to the disk that was previously /dev/sdbx.

So I removed the reformatted disk. Now it is back to the hardware state where it successfully rebooted degraded. Again same failure boot

No amount of tweaking worked and some messages indicated that the superblock was missing. Executing mdadm -D /dev/md0 reported back a normal degraded state raid. I tried shutting down the raid and mounting /dev/sdb1 but got all kinds of ext4 errors. Booted into SystemRescueCD and ran e2fsk and all hell broke loose on the disk check. End result a completely hosed disk.

I'm used to true hardware RAIDs where when a disk breaks you just plug a blank replacement in and the controller takes care of re-syncing. Maybe My mistake was not declaring the sda disk failed before reinstalling blank?

But the whole idea of RAID1 is you've got a complete mirror so what the heck blew the mirror away? Seems I was able to totally kill this rig way too easily.

Love to hear any analysis. BTW the box has an Intel matrix fakeraid. I did not use it because of what I read on forums about how SW raid is superior. Not so sure now.

---

### Post by nerdtron on 2014-08-14
Hardware RAIDs will take care of this easily with no manual intervention. But as you have experienced, software RAID needs to be configured when changing drives.
Have you taken a look on this one [http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

---

