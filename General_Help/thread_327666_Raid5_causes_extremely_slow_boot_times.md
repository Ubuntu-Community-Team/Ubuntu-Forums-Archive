---
title: "Raid5 causes extremely slow boot times"
date: 2006-12-29
forum: General Help
---

### Post by apfsdsdu on 2006-12-29
I installed Kubuntu 6.10 on an old Pentium3 450. It has four hard drives, 3 PATA and one SCSI. The SCSI controller is an Adaptec AHA-2940U. 

I made a small (4.5 GiO x 3)  Raid5 array that uses the devices hda2, hdd2 and sda1. It works exactly like it should, except when the computer boots. Booting takes about 20 minutes and the disks seek furiously the whole time. Dmesg looks like this:

```
[   84.528039] raid5: automatically using best checksumming function: pIII_sse
[   84.546977]    pIII_sse  :   911.000 MB/sec
[   84.546988] raid5: using function: pIII_sse (911.000 MB/sec)
[   84.566531] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   84.566546] md: bitmap version 4.39
[   84.577237] md: raid5 personality registered for level 5
[   84.577253] md: raid4 personality registered for level 4
[   87.659042]  target0:0:2: FAST-20 WIDE SCSI 40.0 MB/s ST (50 ns, offset 8)
[   87.699242] SCSI device sda: 8925000 512-byte hdwr sectors (4570 MB)
[   87.748672] sda: Write Protect is off
[   87.748688] sda: Mode Sense: b9 00 00 08
[   87.781093] SCSI device sda: drive cache: write back
[   87.815521] SCSI device sda: 8925000 512-byte hdwr sectors (4570 MB)
[   87.864962] sda: Write Protect is off
[   87.864979] sda: Mode Sense: b9 00 00 08
[   87.897361] SCSI device sda: drive cache: write back
[   87.897382]  sda: sda1
[   87.903128] sd 0:0:2:0: Attached scsi disk sda
[ 1319.320503] md: md0 stopped.
[ 1319.372951] md: bind<hdd2>
[ 1319.373431] md: bind<sda1>
[ 1319.374035] md: bind<hda2>
[ 1319.405781] raid5: device hda2 operational as raid disk 0
[ 1319.405798] raid5: device sda1 operational as raid disk 2
[ 1319.405810] raid5: device hdd2 operational as raid disk 1
[ 1319.407222] raid5: allocated 3163kB for md0
[ 1319.407236] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[ 1319.407247] RAID5 conf printout:
[ 1319.407256]  --- rd:3 wd:3 fd:0
[ 1319.407266]  disk 0, o:1, dev:hda2
[ 1319.407276]  disk 1, o:1, dev:hdd2
[ 1319.407285]  disk 2, o:1, dev:sda1

```

There are no errors or anything. Shutdowns are done properly. It just sounds like it's rebuilding the whole array or something when it boots.

---

### Post by mumblingsages on 2007-01-06
Did you figure this out? I just rebuilt my file server using edgy and I'm experiencing the exact same thing.

---

