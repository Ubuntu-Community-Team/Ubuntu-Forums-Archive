---
title: "RAID1 setup removes a device on reboot."
date: 2007-05-24
forum: General Help
---

### Post by diesel1 on 2007-05-24
Hi, I have set up a raid1 device using 2 drives.

Everything seems good until I reboot, when I check the raid1 device this is what I get...
diesel1:~$ sudo mdadm --misc --detail /dev/md0

/dev/md0:
        Version : 00.90.03
  Creation Time : Sat May 19 17:25:25 2007
     Raid Level : raid1
     Array Size : 80035712 (76.33 GiB 81.96 GB)
    Device Size : 80035712 (76.33 GiB 81.96 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu May 24 23:04:44 2007
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 6680b9ca:ed09e8f3:362754d7:dddb6558 (local to host diesel1)
         Events : 0.610

    Number   Major   Minor   RaidDevice State
       0       3        2        0      active sync   /dev/hda2
       1       0        0        1      removed


The device removed is /dev/sdb1, a partition of the same size and flagged as linux raid autodetect.

I have had this problem with different drives, the second device is easily added but then takes 45 minutes to resync, anyhow it should just work from boot.

Any help or ideas would be greatly appreciated.

I have searched high and low for a solution to my problem.

Diesel1.

---

### Post by mgrusin on 2007-05-26
Hello, I'm having a similar problem but with a RAID5 array.  It often - but not always - loses one of its drives on reboot, requiring it to be manually added later.  I had thought that a too-small power supply was the problem, but I've just replaced it with a 500W and it looks like I'm still having problems. :(

My next thought is cheap cables (they do seem "wiggly", are there better ones out there?), followed by the perhaps lousy Promise TX4 300 card (again cheap, but I thought it would be OK for software RAID).

Another problem is that although I think I've set it up right, the mdadm monitor daemon never sends me email when a problem occurs...

Not much to go on I know, but if this is a common issue maybe there's a recent bug in the configs or software?

Thanks! -Mike.

---

### Post by psusi on 2007-05-26
I think this is a bug in the startup scripts.  I think the hardware detection is now done asynchronously and the boot scripts end up activating the raid before all of the disks have been detected.

---

### Post by diesel1 on 2007-05-27
Hi all, I tried again to set up my raid1 and it seems to have worked.

I removed mdadm, deleted the partitions and swapped some partitions around, rebooted then installed mdadm and created the array again.

Everything is fine after a data restoration and a test reboot.

I think mdadm was trying to reinitialize the old raid partitions even though they had been reformatted.

Diesel1.

---

