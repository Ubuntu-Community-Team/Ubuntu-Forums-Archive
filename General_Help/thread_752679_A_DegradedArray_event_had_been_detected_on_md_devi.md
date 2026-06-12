---
title: "A DegradedArray event had been detected on md device /dev/md0"
date: 2008-04-11
forum: General Help
---

### Post by Hungry Snail on 2008-04-11
Hi Guys,

I have just received an automated email telling me I have a degraded array, I ran a check on the server and this is the output.

/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Feb 28 16:53:20 2008
     Raid Level : raid1
     Array Size : 159766272 (152.36 GiB 163.60 GB)
    Device Size : 159766272 (152.36 GiB 163.60 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Apr 12 01:52:58 2008
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 10025f03:8f9f905f:456f4d9a:8fcc0ffe
         Events : 0.4951400

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        -      removed


root@server1:~# cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 sda2[0] sdb2[1]
      39375232 blocks [2/2] [UU]

md0 : active raid1 sda1[0]
      159766272 blocks [2/1] [U_]

unused devices: <none>


Im still relatively new to software raid, the logs show the following..

kernel: [42949381.230000] md: md0 stopped.
kernel: [42949381.230000] md: bind<sdb1>
kernel: [42949381.230000] md: bind<sda1>
kernel: [42949381.230000] md: kicking non-fresh sdb1 from array!
kernel: [42949381.230000] md: unbind<sdb1>
kernel: [42949381.230000] md: export_rdev(sdb1)
kernel: [42949381.230000] raid1: raid set md0 active with 1 out of 2 mirrors
kernel: [42949381.240000] md: md1 stopped.
kernel: [42949381.240000] md: bind<sdb2>
kernel: [42949381.240000] md: bind<sda2>
kernel: [42949381.240000] raid1: raid set md1 active with 2 out of 2 mirrors
kernel: [42949381.260000] Attempting manual resume
kernel: [42949381.320000] kjournald starting.  Commit interval 5 seconds
kernel: [42949381.320000] EXT3-fs: mounted filesystem with ordered data mode

as you can see, it tells me it is kicking sbd1 from the raid, but then goes on to tell me md1 is active with 2 out of 2 mirrors.

Any help on what to do would be appreciated, is this a serious issue? :)

Cheers

---

### Post by fjgaude on 2008-04-12
Seems to me you have a bad drive, one of the two.

You can physically take one out and see what happens. If nothing then you were lucky and took out the bad one the first time around. If the array doesn't come up replace the one taken out as it is the good drive and take the other out. Else you can get the serial number of the bad drive and then take it out. Use 

```
hdparm -i -v /dev/md[nn]
```

to get the SN of the drive. Then local that number on the drive and remove it.

That's about all I can suggest. Unless you wish to try to repair the bad drive. If so, leave it in, make sure you have a backup of your data, and run fsck on the array.

Let us know how you are doing.

---

