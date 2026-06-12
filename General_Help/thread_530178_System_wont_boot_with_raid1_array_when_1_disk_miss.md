---
title: "System wont boot with raid1 array when 1 disk missing"
date: 2007-08-20
forum: General Help
---

### Post by somafm on 2007-08-20
Hello,

I have seen a few posts with people who had this problem, but have not seen anything that would fix it. I have a system running Ubuntu 7.04 with 2 500GB sata drives in RAID1 (mirror). The RAID1 is the built in software linux raid (not sure what you technically call it) that you setup when installing. Was pretty easy to setup after reading a few guides, and it worked great. After the install I simulated a disk failure by unplugging unplugging 1 disk. The system rebooted just fine, and the command **cat /proc/mdstat** reported 1 device missing. I rebooted again after plugging the device in and it automatically booted up, and another **cat /proc/mdstat** reported that the array was being rebuilt. So it worked perfectly, and I left it alone!

After a few months of using the system, updating when there were new updates, and not messing with anything critical, I decided to give the RAID1 another failure test. I shut down and unplugged a random drive. When booting back up, it just sat at the Ubuntu loading screen for a few minutes and finally went into the 'initramfs busybox shell'. This is pretty much _[identical to the issue here]("http://ubuntuforums.org/archive/index.php/t-420993.html")_, except he was able to boot from the busybox shell with 1 disk, and I can't.

After shutting down and plugging the drive back in, the system boots up perfectly again. No rebuilds need to be done either, so it's like nothing ever happened. But now I sit with a system that has no fault tolerance, and worry :-P. No matter which drive I unplug, they both do this same thing.

Does anyone know what would cause this, or what I can do to fix it? The link I posted above said to submit it as a bug report, but that was back in April so if it was a bug I think more people would have reported it by now and we would have seen a fix.

I don't know what other information to provide, so let me know if you need any more info and I'd be glad to provide it. Just be specific on how to find it because I may not know :-P

Thanks!

---

### Post by somafm on 2007-08-20
Here is a bit of info, not sure if it will help:

**_cat /proc/mdstat_**
```
md0 : active raid1 sda1[0] sdb1[1]
485347648 blocks [2/2] [UU]
```

**_the array line inside my mdadm.conf file_**
```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=4a8cc41b:220054e9:fec14e1d:c7b1c5dc
```

**_sudo mdadm --query --detail /dev/md0_**
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Fri Apr 20 07:05:41 2007
     Raid Level : raid1
     Array Size : 485347648 (462.86 GiB 497.00 GB)
    Device Size : 485347648 (462.86 GiB 497.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Aug 20 06:57:58 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 4a8cc41b:220054e9:fec14e1d:c7b1c5dc
         Events : 0.1880

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
```

---

### Post by fjgaude on 2007-08-20
I'm no expert and don't use raid1 but do raid5, but I've read enough posts similar to your problem to think that this is a Linux issue. The software raid in Linux is normally called md for Multiple Devices, as RAID is really a poor, but conventional, way to describe reliable arrays.

Likely this issue will be fixed in upcoming releases of either the kernel or the md package.

Hang in there,

frank

---

### Post by somafm on 2007-08-20
Alright, thanks so much for the reply :cool:. I went ahead and filed a bug report just in case. And if it gets filed as a dupe, at least we will know they are aware, and a fix is coming!

---

