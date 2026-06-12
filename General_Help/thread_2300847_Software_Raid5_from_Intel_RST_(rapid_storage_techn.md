---
title: "Software Raid5 from Intel RST (rapid storage technology) problem"
date: 2015-10-28
forum: General Help
---

### Post by michi1983 on 2015-10-28
Hey guys,

If this thread is in the wrong section, please feel free to move it. I just wasn't sure if it fits here or not.

TL;DR: **I can't access my Software Raid5 (neither in Windows nor Linux).**

So, I have 4 disks in my computer.
1 Intel SSD on which is my Windows 10 Pro 64bit system.
3 SATA discs (2 with 640 GB and one 1TB).
I used the Intel RST software to create a fakeraid (Raid5).
To enter this setup I have to hit the CTRL+I keys while the pc boots up and then this screen appears.
[ATTACH=CONFIG]265220[/ATTACH]

So this tells me, that the Raid **should** be alright.
When I boot up Windows it just doesn't show up.
So I tried to boot up a linux live system to see what's wrong.

Unfortunately, a ```
cat /proc/mdstat
``` brings nothing than:
```
Personalities : [raid10] [raid1] [raid6] [raid5] [raid4]  
unused devices: <none>
```

The Raid consists of /dev/sda /dev/sdb and /dev/sdc which in my opinion is confirmed by the output of ```
sudo blkid
```
```
/dev/sda: TYPE="isw_raid_member"  
/dev/sdb: TYPE="isw_raid_member"  
/dev/sdc: TYPE="isw_raid_member" 
```

Even dmesg shows me this:
```
[    4.037563] raid6: sse2x1   11417 MB/s 
[    4.105549] raid6: sse2x2   14585 MB/s 
[    4.173520] raid6: sse2x4   16832 MB/s 
[    4.241501] raid6: avx2x1   22266 MB/s 
[    4.309484] raid6: avx2x2   25577 MB/s 
[    4.377460] raid6: avx2x4   29686 MB/s 
[    4.377461] raid6: using algorithm avx2x4 (29686 MB/s) 
[    4.377462] raid6: using avx2x2 recovery algorithm 
[    4.418534] md: raid10 personality registered for level 10 
[    4.419506] md: raid1 personality registered for level 1 
[    4.424125] md: raid6 personality registered for level 6 
[    4.424127] md: raid5 personality registered for level 5 
[    4.424127] md: raid4 personality registered for level 4 
[    4.424891] device-mapper: raid: Loading target version 1.6.0 
[    4.425478] md/raid:mdX: device sda operational as raid disk 2 
[    4.425479] md/raid:mdX: device sdc operational as raid disk 1 
[    4.425480] md/raid:mdX: device sdb operational as raid disk 0 
[    4.425643] md/raid:mdX: allocated 0kB 
[    4.425662] md/raid:mdX: raid level 5 active with 3 out of 3 devices, algorithm 0
```
which (at least to me) looks like the raid is kind of active and consists of 3 devices.

An additional ```
mdadm --examine /dev/sdb
``` shows me this:
```
/dev/sdb: 
          Magic : Intel Raid ISM Cfg Sig. 
        Version : 1.2.02 
    Orig Family : 374dea34 
         Family : 5f84eb44 
     Generation : 0033bd09 
     Attributes : All supported 
           UUID : cab60d47:4a8c4a59:ec3b7b42:5f3a6740 
       Checksum : e2fae08e correct 
    MPB Sectors : 2 
          Disks : 3 
   RAID Devices : 1 
  
  Disk00 Serial : WD-WCC4JHSZ79DY 
          State : active 
             Id : 00020000 
    Usable Size : 1953518862 (931.51 GiB 1000.20 GB) 
  
[Cover-Direct]: 
           UUID : 25254606:dc7c3954:5c44f2e1:f7b93773 
     RAID Level : 5 
        Members : 3 
          Slots : [UUU] 
    Failed disk : none 
      This Slot : 0 
     Array Size : 2500517888 (1192.34 GiB 1280.27 GB) 
   Per Dev Size : 1250259208 (596.17 GiB 640.13 GB) 
  Sector Offset : 0 
    Num Stripes : 4883824 
     Chunk Size : 128 KiB 
       Reserved : 0 
  Migrate State : idle 
      Map State : normal 
    Dirty State : clean 
  
  Disk01 Serial : WD-WMASY7185466 
          State : active 
             Id : 00050000 
    Usable Size : 1250257422 (596.17 GiB 640.13 GB) 
  
  Disk02 Serial : WD-WMASY7045144 
          State : active 
             Id : 00010000 
    Usable Size : 1250257422 (596.17 GiB 640.13 GB)
```
The corresponding result do I get when I exchange /dev/sdb with /dev/sda and /dev/sdc

What I might need to mention is that I have no clue anymore if I initially created the Raid with a partition table or the whole raw discs, but I assume it was the latter. 

As kind of last resort I tried this command (because of research in the net):
```
mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sda
``` but it failed because it tells me that there are no superblocks on the device /dev/sdb.
Same result when I switch the devices. So it doesn't matter which device I chose first it tells me there are no superblocks on either /dev/sda, /dev/sdb or /dev/sdc.

The worst thing is that I don't have a backup of these files because I was the opinion that my Raid5 (even when it's only software) is kinda safe.
But as often, reality proofed me wrong.

Do you guys have any idea how I could recover the Raid without losing the data on it?
In some places there still is information about the Raid or am I wrong?

I appreciate every piece of help I can get.
If I can assist with further infos please let me know.

Here is the output of ```
sudo dmraid -tay
```
```
isw_bgacfegfaa_Cover-Direct: 0 2500518400 raid raid5_la 4 256 nosync region_size 131072 3 - /dev/sdb - /dev/sdc - /dev/sda
```

Doesn't this mean that the system still recognizes the Raid5?

And here is the output of ```
sudo cat /etc/mdadm/mdadm.conf
```
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY metadata=imsm UUID=cab60d47:4a8c4a59:ec3b7b42:5f3a6740
ARRAY /dev/md/Cover-Direct container=cab60d47:4a8c4a59:ec3b7b42:5f3a6740 member=0 UUID=25254606:dc7c3954:5c44f2e1:f7b93773

# This file was auto-generated on Thu, 29 Oct 2015 08:35:10 +0000
# by mkconf $Id$

```

I even tried to force it to reassable with ```
sudo mdadm --assemble --run --force /dev/md/Cover-Direct /dev/sdb /dev/sdc /dev/sda
```
but it failed with the following output:
```
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted

```

I'm running out of ideas :???:

Regards,
Michael

---

