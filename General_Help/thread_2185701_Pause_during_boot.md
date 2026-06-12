---
title: "Pause during boot"
date: 2013-11-03
forum: General Help
---

### Post by XBNCPRk on 2013-11-03
I ran bootchart recently to look for ways to speed up the boot on a media server, and noticed there was what looks like about a 5 second pause during the boot thats marked as 'wait-for-root'.  Its the only process thats appears to be running during that time, and Im not entirely sure what it is, or how to eliminate it. The system boots and runs from an ssd, and uses a fairly large mdadm raid5 array for storage. I cant imagine though that either of those would take 5 seconds to do anything (far less than that for the ssd to check anything, longer for the array)...
[IMG]http://tinypic.com/r/axgxo8/5[/IMG]
Any help would be appreciated...

---

### Post by XBNCPRk on 2013-11-05
*bump*

Anyone know what the long (~5sec) pause is during the boot? I see it on most of the bootcharts posted but not on all, so it definitely seems to be a user-changeable setting, and it seems to be running concurrently with udevd so Im assuming its something on one of the udev rules...

---

### Post by oldfred on 2013-11-05
I never learned to read boot chart, but I do look at log file for repeated task, out right errors or long times between tasks.

I look in /var/log/demesg

---

### Post by XBNCPRk on 2013-11-06
> **oldfred said:**
> I never learned to read boot chart, but I do look at log file for repeated task, out right errors or long times between tasks.

I look in /var/log/demesg


The only long time between tasks that I can find in the dmesg log is a gap of about 6.4 seconds while its mounting a raid5 array. This does correspond to the time marked on the bootchart output as being basically inactive and the 'wait-for-root' process that Im curious about. 
 
```
[    3.210690] md: bind<sdg1>[    3.212683] bio: create slab <bio-1> at 1
[    3.212695] md/raid:md1: device sdg1 operational as raid disk 3
[    3.212697] md/raid:md1: device sdb1 operational as raid disk 0
[    3.212699] md/raid:md1: device sdd1 operational as raid disk 2
[    3.212700] md/raid:md1: device sdc1 operational as raid disk 1
[    3.212702] md/raid:md1: device sde1 operational as raid disk 5
[    3.212703] md/raid:md1: device sda1 operational as raid disk 4
[    3.213033] md/raid:md1: allocated 6384kB
[    3.213060] md/raid:md1: raid level 5 active with 6 out of 6 devices, algorithm 2
[    3.213062] RAID conf printout:
[    3.213063]  --- level:5 rd:6 wd:6
[    3.213064]  disk 0, o:1, dev:sdb1
[    3.213065]  disk 1, o:1, dev:sdc1
[    3.213067]  disk 2, o:1, dev:sdd1
[    3.213068]  disk 3, o:1, dev:sdg1
[    3.213069]  disk 4, o:1, dev:sda1
[    3.213070]  disk 5, o:1, dev:sde1
[    3.213092] md1: detected capacity change from 0 to 10001973248000
[    3.213987]  md1: unknown partition table
[    8.634732] EXT4-fs (sdf1): mounted filesystem with ordered data mode. Opts: (null)
[   10.856478] EXT4-fs (sdf1): re-mounted. Opts: discard,errors=remount-ro
[   11.294719] kjournald starting.  Commit interval 5 seconds
[   11.300344] EXT3-fs (md1): using internal journal
[   11.300349] EXT3-fs (md1): mounted filesystem with ordered data mode
```

Not entirely sure what that implies though... Is it taking that long to mount the raid array without errors, and if so, is that normal?

---

### Post by oldfred on 2013-11-06
Do not know anything about RAID, but that may be normal. 
I know when I add a NTFS mount to fstab my boot slows a lot or as much as 5 sec on a 20 sec boot with a SSD. But I assume that is because it is NTFS and not native. What is a bit strange is on a hard drive boot of 40 sec it still is about a 5 sec delay??

---

### Post by XBNCPRk on 2013-11-06
> **oldfred said:**
> Do not know anything about RAID, but that may be normal. 
I know when I add a NTFS mount to fstab my boot slows a lot or as much as 5 sec on a 20 sec boot with a SSD. But I assume that is because it is NTFS and not native. What is a bit strange is on a hard drive boot of 40 sec it still is about a 5 sec delay??

Ah, I think you may have answered my question, knowingly or not... Part of my fstab file is mounting a network attached drive using curlftp. Obviously though since the wifi isnt up and connected at that point, that mount would fail (its later mounted by a command in my rc.local file) but assumably it would wait a few seconds to keep retrying before bypassing it and moving on with the rest of the boot.

Edit: Nope, I was wrong...it does delay it while failing that mount, but only by about 1/2 a second judging by the change in boot times when I comment that line out of the fstab file. 

The systems single boot 12.04 on an ssd, with a 6x2tb raid 5 array (which is sadly full), but I cant imagine its taking a second each to spin up the disks and assemble the array to run.

---

