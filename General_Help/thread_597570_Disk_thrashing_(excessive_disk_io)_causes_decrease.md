---
title: "Disk thrashing (excessive disk i/o) causes decrease/loss of responsiveness in Gutsy 7"
date: 2007-10-30
forum: General Help
---

### Post by b5baxter on 2007-10-30
I am  experiencing disk thrashing with the following characteristics.
- Starts randomly and does not seem to be associated with a specific application (although often occurs when Firefox or App Updater are running).
- Mouse becomes very slow  to respond
- Keyboard becomes extremely slow or unresponsive
- screen becomes unresponsive
- often requires a power down
- Tracker has been disabled
- Compaq Presario R3000 with AMD 64 
- Install of Gutsy 7.1 on new partition
- Dual boots to Windows XP with no disk problems
- Fedora 7 was previously installed on same machine with no disk problems.
- System Monitor (and Htop) shows 100% CPU but all listed tasks are only using a small fraction of the CPU.  Swap is not being used.  (But may not be accurate because often screen freezes when the thrashing starts).
- tried disabling APM for disks using “ hdparm -B 255 /dev/hda” but this did not effect the bug.

---

### Post by dcstar on 2007-10-31
> **b5baxter said:**
> I am  experiencing disk thrashing with the following characteristics.
- Starts randomly and does not seem to be associated with a specific application (although often occurs when Firefox or App Updater are running).
- Mouse becomes very slow  to respond
- Keyboard becomes extremely slow or unresponsive
- screen becomes unresponsive
- often requires a power down
- Tracker has been disabled
- Compaq Presario R3000 with AMD 64 
- Install of Gutsy 7.1 on new partition
- Dual boots to Windows XP with no disk problems
- Fedora 7 was previously installed on same machine with no disk problems.
- System Monitor (and Htop) shows 100% CPU but all listed tasks are only using a small fraction of the CPU.  Swap is not being used.  (But may not be accurate because often screen freezes when the thrashing starts).
- tried disabling APM for disks using “ hdparm -B 255 /dev/hda” but this did not effect the bug.

When it occurs open a terminal and run **top**, it will show you what is using all the CPU.

---

### Post by nowshining on 2007-10-31
it's most likely tracker an automatic disk indexing service/app open up session and remove it and then do a reboot. OR it's updatedb indexing ur files via a cron job. IF u don't want crons running u can stop it from starting up and then u'll have to do it manually by opening up a terminal and typing updatedb and pressing enter.

---

### Post by b5baxter on 2007-10-31
> **dcstar said:**
> When it occurs open a terminal and run **top**, it will show you what is using all the CPU.

Thanks for your reply.

Most of the time the system is so unresponsive I have not been able to do that.  On the couple of occasions I have TOP shows no applications above 3% CPU - yet the hard drive light is on almost constantly and the system is unresponsive.

---

### Post by bingoUV on 2007-10-31
> **b5baxter said:**
> Thanks for your reply.

Most of the time the system is so unresponsive I have not been able to do that.  On the couple of occasions I have TOP shows no applications above 3% CPU - yet the hard drive light is on almost constantly and the system is unresponsive.

Yes, when there is too much disk activity, the system will be unresponsive even if CPU utilization is not high. You can see this in top, Cpu(s) row, something like 
```

Cpu(s): 12.3%us,  2.3%sy,  0.0%ni, 85.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

```

The "wa" suggests that there is too much of I/O activity going on (it is zero in the above example but it will be high if disk activity LED is glowing a lot). 

At such time, a good guess will be that the process which is taking 1 or 2% of CPU is the culprit. It would likely have requested a large I/O.

---

### Post by b5baxter on 2007-11-01
> **nowshining said:**
> it's most likely tracker an automatic disk indexing service/app open up session and remove it and then do a reboot. OR it's updatedb indexing ur files via a cron job. IF u don't want crons running u can stop it from starting up and then u'll have to do it manually by opening up a terminal and typing updatedb and pressing enter.

Thanks for your reply.

As I mentioned in the first post - tracker is disabled.
I tried turning of crons and still have the problem.

---

### Post by b5baxter on 2007-11-06
> **bingoUV said:**
> Yes, when there is too much disk activity, the system will be unresponsive even if CPU utilization is not high. ...
At such time, a good guess will be that the process which is taking 1 or 2% of CPU is the culprit. It would likely have requested a large I/O.

Thanks for clearing that up...

The following processes seem to be in the top 10 most often when the thrashing occurs:
- kswapd0
- hald
- kthreadd

---

### Post by b5baxter on 2007-11-09
Okay, I think I found out what the problem was.  The sway partition was turned off!

I feel sorta stupid but I just assumed because it was a realatively new installation and I had not changed anything with the swap that the swap was on.  But I went to Ssytem -> Administration -> Partition Editor (gparted) -> Right clicked on the Swap partition -> Infomration -> and it showed "Inactive".  So, I right clicked on it again and chose "swapon"

This seemed to clear it up for a few reboots.

But ... then the thrashing came back. I went back into the Partition Editor and the swap had been turned off again.  This has happened now a few times after I reboot the system.

So, what would be causing the swap to be turned off???

---

### Post by b5baxter on 2007-11-10
> **b5baxter said:**
> 
So, what would be causing the swap to be turned off???

So it looks like it is all solved now.

The thrashing was caused by the swap not being turned on properly.

The swap was not turned on because fstab had the wrong UUID.```

```

Fixed based on instructions here: [http://ubuntuforums.org/showthread.php?p=3704872](http://ubuntuforums.org/showthread.php?p=3704872)

- type ```
blkid
```
- note the UUID of the partition that should be the swap
- edit /etc/fstab so that the UUID matches

---

