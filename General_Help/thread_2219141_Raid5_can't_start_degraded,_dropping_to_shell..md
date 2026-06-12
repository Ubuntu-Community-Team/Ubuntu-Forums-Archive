---
title: "Raid5 can't start degraded, dropping to shell."
date: 2014-04-23
forum: General Help
---

### Post by Benjamin_Bugten on 2014-04-23
Hello!


I've been running Ubuntu Server 12.04 in Raid5 (6 disks) for a year or so. It's mainly used for storage and as a Plex media server.
I still consider myself pretty much a n00b, but using guides I've managed so far.
  The server's been working fine for the most part, except for when one of my HDD's died a couple months ago. I replaced the disk, added it to the raid and synced it back up - no problem.


A few days ago the server stopped responding. I was forced to shut it down with the power button and it wouldn't come back up.
Starting in recovery mode it went like this:


```

md: bind<sda1>
md: bind<sdf3>
md: bind<sdd3>
md: bind<sdc1>
md: bind<sda2>
md: bind<sdc3>
md: bind<sdb2>
md: bind<sdf1>
md: bind<sdb3>
md: bind<sde1>
md: kicking non-fresh sdb1 from array!
md: unbind<sdb1>
md: export_rdev(sdb1)
bio: create slab <bio-1> at 1
md/raid:md0: device sde1 operational as raid disk 4
md/raid:md0: device sdf1 operational as raid disk 5
md/raid:md0: device sdc1 operational as raid disk 2
md/raid:md0: device sda1 operational as raid disk 0
md/raid:md0: device sdd1 operational as raid disk 3
md/raid:md0: allocated 6300kB
md/raid:md0: raid level 5 active with 5 out of 6 devices, algorithm 2
md0: detected capacity change from 0 to 7987527680
md0: unknown partition table
** WARNING: There appears to be one or more degraded RAID devices **


The system may have suffered a hardware fault, such as a disk drive failure. The root device may depend on the RAID devices being online. One or more of the the following RAID devices are degraded:
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sde1[6] sdf1[5] sdc1[2] sda1[0] sdd1[3]
      7800320 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/5] [U_UUUU]


md2 : inactive sdb3[1](S) sdc3[2](S) sdd3[3](S) sdf3[5](S) sde3[6](S) sda3[0](S)
      11653109760 blocks super 1.2


md1 : inactive sdb2[1](S) sda2[0](S) sdd2[3](S) sdc2[2](S) sdf2[5](S) sde2[6](S)
      58589184 blocks super 1.2


unused devices: <none>
You may attempt to start the system anyway, or stop now and attempt manual recovery operations. to do this automatically in the future, add "bootdegraded=true" to the kernel boot options.


If you choose to start the degraded RAID, the system may boot normally, but performance may be degraded, and a further hardware fault could result in permanent data loss.


If you abort now, you will be provided with a recovery shell.


Do you wish to start the degraded RAID? [y/N]: y
Attempting to start the RAID in degraded mode...
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
md: kicking non-fresh sdc3 from array!
md: unbind<sdc3>
md: export_rdev(sdc3)
md: kicking non-fresh sdd3 from array!
md: unbind<sdd3>
md: export_rdev(sdd3)
md/raid:md2: device sdb3 operational as raid disk 1
md/raid:md2: device sdf3 operational as raid disk 5
md/raid:md2: device sde3 operational as raid disk 4
md/raid:md2: device sda3 operational as raid disk 0
md/raid:md2: allocated 6300kB
md/raid:md2: not enough operational devices (2/6 failed)
md/raid:md2: failed to run raid set.
md: pers->run() failed ...
mdadm: failed to start aray /dev/md/2: Input/output error
md: kicking non-fresh sdd2 from array!
md: unbind<sdd2>
md: export_rdev(sdd2)
md: kicking non-fresh sdc2 from array!
md: unbind<sdc2>
md: export_rdev(sdc2)
md/raid:md1: device sdb2 operational as raid disk 1
md/raid:md1: device sda2 operational as raid disk 0
md/raid:md1: device sdf2 operational as raid disk 5
md/raid:md1: device sde2 operational as raid disk 4
md/raid:md1: allocated 6300kB
md/raid:md1: not enough operational devices (2/6 failed)
md/raid:md1: failed to run raid set.
md: pers->run() failed ...
mdadm: failed to start array /dev/md/1: Input/output error
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
/dev/md/0 is already in use.
/dev/md/1 is already in use.
/dev/md/2 is already in use.
Could not start the RAID in degraded mode.
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; is /dev)
ALERT! /dev/disk/by-uuid/ce309028-ce00-4cb5-a6d6-c66ab2480acf does not exist.
Dropping to a shell!


BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)
Enter 'help' for a list of built-in commands.


(initramfs)

```
I tried finding a solution by googling the various error messages, but couldn't find anything exactly like my own problem.
Based on my experiences with one drive dying, I noticed md0 was missing drive sdb1, so I did:
```
mdadm --manage /dev/md0 --add /dev/sdb1
```
I'm thinking this probably wasn't the correct thing to do as when I tried to assemble the raid I got an error message saying something along the lines of md0 containing multiple drives with same ID. I can't remember exactly, and I'm scared of doing anything else at this point and thought instead I would seek help.

cat /proc/mdstat as it stands:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[2] sda1[0] sdf1[5] sdb1[7] sdd1[3] sde1[6]
      7800320 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/6] [UUUUUU]


md2 : inactive sdf3[5] sdb3[1] sda3[0] sde3[6]
      7768739840 blocks super 1.2


md1 : inactive sdb2[1] sda2[0] sde2[6] sdf2[5]
      39059456 blocks super 1.2

unused devices: <none>

```

Any help would be greatly appreciated :)

---

