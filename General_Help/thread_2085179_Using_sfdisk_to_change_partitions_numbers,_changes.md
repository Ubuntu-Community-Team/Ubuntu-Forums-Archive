---
title: "Using sfdisk to change partitions numbers, changes not being applied"
date: 2012-11-17
forum: General Help
---

### Post by Mr_JMM on 2012-11-17
Hi,

I've included a thumbnail of gparted screenshot to help visualise the following (taken from a LiveUSB of Parted Magic):

sudo fdisk -l
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04380438

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     4196351     2097152   82  Linux swap
/dev/sda2   *     5244928    30410751    12582912   83  Linux
/dev/sda3         4196352     5244927      524288   83  Linux
/dev/sda4        30410752   625139711   297364480    5  Extended
/dev/sda5        30412800    55578623    12582912   83  Linux
/dev/sda6        55580672    80746495    12582912   83  Linux
/dev/sda7        80748544   105914367    12582912   83  Linux
/dev/sda8       332423168   625139711   146358272   83  Linux
/dev/sda9       105916416   210774015    52428800   83  Linux
/dev/sda10      210776064   235941887    12582912   83  Linux
/dev/sda11      235943936   261109759    12582912   83  Linux
/dev/sda12      261111808   286277631    12582912   83  Linux
/dev/sda13      286279680   311445503    12582912   83  Linux
/dev/sda14      311447552   321933311     5242880   83  Linux
/dev/sda15      321935360   332421119     5242880   83  Linux

```

Partition Table (sudo sfdisk -d /dev/sda > Desktop/PT.txt)
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  4194304, Id=82
/dev/sda2 : start=  5244928, size= 25165824, Id=83, bootable
/dev/sda3 : start=  4196352, size=  1048576, Id=83
/dev/sda4 : start= 30410752, size=594728960, Id= 5
/dev/sda5 : start= 30412800, size= 25165824, Id=83
/dev/sda6 : start= 55580672, size= 25165824, Id=83
/dev/sda7 : start= 80748544, size= 25165824, Id=83
/dev/sda8 : start=332423168, size=292716544, Id=83
/dev/sda9 : start=105916416, size=104857600, Id=83
/dev/sda10: start=210776064, size= 25165824, Id=83
/dev/sda11: start=235943936, size= 25165824, Id=83
/dev/sda12: start=261111808, size= 25165824, Id=83
/dev/sda13: start=286279680, size= 25165824, Id=83
/dev/sda14: start=311447552, size= 10485760, Id=83
/dev/sda15: start=321935360, size= 10485760, Id=83

```

I edited the table to:
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=  4194304, Id=82
/dev/sda3 : start=  5244928, size= 25165824, Id=83, bootable
/dev/sda2 : start=  4196352, size=  1048576, Id=83
/dev/sda4 : start= 30410752, size=594728960, Id= 5
/dev/sda5 : start= 30412800, size= 25165824, Id=83
/dev/sda6 : start= 55580672, size= 25165824, Id=83
/dev/sda7 : start= 80748544, size= 25165824, Id=83
/dev/sda15: start=332423168, size=292716544, Id=83
/dev/sda14: start=105916416, size=104857600, Id=83
/dev/sda8 : start=210776064, size= 25165824, Id=83
/dev/sda9 : start=235943936, size= 25165824, Id=83
/dev/sda10: start=261111808, size= 25165824, Id=83
/dev/sda11: start=286279680, size= 25165824, Id=83
/dev/sda12: start=311447552, size= 10485760, Id=83
/dev/sda13: start=321935360, size= 10485760, Id=83

```

I then attempt to re-write the partition table by using:
```
sudo swapoff -a
sudo sfdisk /dev/sda < Desktop/PT2.txt
```

It runs, displays lots of errors about the partitions not starting or ending on a cylinder (I partition to MiB) and says it was successful. However nothing changes either before or after a reboot?

Not that it's relavent but someone will ask...
I wanted the two largest partitions to be 14 and 15 then everything else in number order. Looking at the GParted image you'd get:
sda1,2,3,4 (Extended),5,6,7,14,8,9,10,11,12,13,15.
And to answer the other not relevant question that someone will ask: Because I'm playing in effort to learn and why not?

Am I doing something wrong or can anyone see anything else that might be causing this issue?
The only obvious error is the 
```

Warning: Partition [x] does not start at a cylinder boundary
Warning: Partition [x] does not end at a cylinder boundary
Warning: Partition x does not end at a cylinder boundary
```
But I didn't think we still had to do that when partitioning but are instead advised to "Align to MiB"??

There is something else; after trying to apply the edited table, at the end there is a message:
```
If you created or changed a DOS partition, /dev/foo7, say, then use dd(1) to zero the first 512 bytes: [shows code]
```
I didn't want to do this without checking with you guys first that this applies to me.

---

### Post by Mr_JMM on 2012-11-20
Bump

---

### Post by oldfred on 2012-11-20
And why?

I have not used sfdisk to fix, but have some notes (as usual :) ) Caljohsmith contributed to bootinfoscript, so he knows lots of details on systems.
I think you are missing some parameters?

       Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Equivalent sfdisk values would keep the start point and convert the end point via the formula size = end - start + 1. 
Also fdisk -lu shows start & blocks, blocks * 2 also equals size in sectors

   Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

