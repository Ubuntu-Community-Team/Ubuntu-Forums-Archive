---
title: "HDD Has Disappeared (Dual Boot: Windows 7 / Ubuntu 12)"
date: 2014-04-13
forum: General Help
---

### Post by AmagicalFishy on 2014-04-13
Hey, everyone.  I've got an HP Elitebook 8460p, about a year old, and I've been dual-booting Windows 7 and Ubuntu w/ Grub 2 for a while; I use them both pretty often. Here's what happened:

Last night, I was playing some Dwarf Fortress (on Windows) and suddenly: **BSOD**. The physical memory dump failed (which I've never seen before) and the computer restarted. When it came to, I got a black screen with white text saying something like *"Please install operating system on HDD: hd03"* From there, the computer went to some HP System Diagnostics tool, and the HDD Test immediately fails (though admittedly I'm not sure what it's diagnosing). The BIOS doesn't recognize that there's an HDD in at all. 

Currently, I'm using Ubuntu "Try Before Installing" on a USB-drive, since my whole HDD seems shot. *Nothing* recognizes that my HDD is even connected, except this:
```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda1

Disk /dev/sda1: 7795 MB, 7795628032 bytes
241 heads, 62 sectors/track, 1018 cylinders, total 15225836 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda


This doesn't look like a partition table
Probably you selected the wrong device.


     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sda1p2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
/dev/sda1p3   ?           0           0           0   6f  Unknown
/dev/sda1p4        50200576   974536369   462167897    0  Empty


Partition table entries are not in disk order



```
Now, the way my computer was set up was that HP had 3 partitions; the main one and the two diagnostic/recovery partitions. Then, when I installed Ubuntu, I let it do its own thing as installing alongside another OS. If I remember correctly, I created another logical partition or something of the sort. The above "partition table" tells me that there is *something* there, and I really need to use that to get myself into a workable position. Do yo guys have any suggestions? I could really, really, really use some expert help. I've tried testdisk, and it doesn't see my HDD at all. I can fdisk into /dev/sda1, though.

I'm by no means an expert (or even very good) at Ubuntu, but I've used computers for a long time, and have run into many  seemingly irrecoverable problems. Unfortunately, a *lot* of my time is spent scrolling through threads where the suggestion is ultimately "Looks like you need to buy a new harddrive." I've fixed all of the problems and have never needed to buy a new HDD. :l
 
I'm just not sure how to approach this one, and could really use some help. This is my first time attempting to fix anything with Ubuntu instead of Ultimate Boot CD for Windows or something. (If it's of any assistance, something like this happened to a friend's computer a year or two ago and I used a combination of seemingly obscure programs in Ultimate Boot CD which eventually allowed Testdisk to see the HDD and ultimately fix things up; if anyone's familiar w/ those programs, maybe their Linux equivalent could help?)

---

### Post by SuperFreak on 2014-04-13
You might want to check SMART attributes , I think it is listed in Dash under Disks or Disk Utility

---

### Post by AmagicalFishy on 2014-04-13
Disk Utility doesn't see the HDD either. I installed the appropriate package and:
```
ubuntu@ubuntu:~$ sudo smartctl -iT permissive /dev/sda1smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.11.0-15-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


Vendor:                       
Product:              USB Flash Memory
Revision:             PMAP
User Capacity:        7,803,174,912 bytes [7.80 GB]
Logical block size:   512 bytes
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page

```

```
ubuntu@ubuntu:~$ sudo smartctl -a -d ata -T permissive /dev/sda1smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.11.0-15-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


Smartctl: Device Read Identity Failed: Invalid argument


=== START OF INFORMATION SECTION ===
Device Model:     [No Information Found]
Serial Number:    [No Information Found]
Firmware Version: [No Information Found]
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   [No Information Found]
ATA Standard is:  [No Information Found]
Local Time is:    Sun Apr 13 23:04:59 2014 UTC
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 82-83 don't show if SMART supported.
SMART support is: Ambiguous - ATA IDENTIFY DEVICE words 85-87 don't show if SMART is enabled.
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

```

It sees *something*. :(

---

### Post by presence1960 on 2014-04-13
> **AmagicalFishy said:**
> Hey, everyone.  I've got an HP Elitebook 8460p, about a year old, and I've been dual-booting Windows 7 and Ubuntu w/ Grub 2 for a while; I use them both pretty often. Here's what happened:

Last night, I was playing some Dwarf Fortress (on Windows) and suddenly: **BSOD**. The physical memory dump failed (which I've never seen before) and the computer restarted. When it came to, I got a black screen with white text saying something like *"Please install operating system on HDD: hd03"* From there, the computer went to some HP System Diagnostics tool, and the HDD Test immediately fails (though admittedly I'm not sure what it's diagnosing). The BIOS doesn't recognize that there's an HDD in at all. 

Currently, I'm using Ubuntu "Try Before Installing" on a USB-drive, since my whole HDD seems shot. *Nothing* recognizes that my HDD is even connected, except this:
```
**ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda1**

Disk /dev/sda1: 7795 MB, 7795628032 bytes
241 heads, 62 sectors/track, 1018 cylinders, total 15225836 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda


This doesn't look like a partition table
Probably you selected the wrong device.


     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sda1p2   ?  3272020941  5225480974   976730017   16  Hidden FAT16
/dev/sda1p3   ?           0           0           0   6f  Unknown
/dev/sda1p4        50200576   974536369   462167897    0  Empty


Partition table entries are not in disk order



``` 

The command to run is ```
sudo fdisk -l
``` the command you ran which is highlighted in bold above is looking for a single partition partition instead of the partition table for the disk.Here is my output from both commands. Notice the difference:

```
raz@raz-A75F2-A2:~$ sudo fdisk -l /dev/sda3
[sudo] password for raz: 

Disk /dev/sda3: 28.8 GB, 28764536832 bytes
255 heads, 63 sectors/track, 3497 cylinders, total 56180736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda3 doesn't contain a valid partition table

**raz@raz-A75F2-A2:~$ sudo fdisk -l**

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7408b4a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   142608383    71303168    7  HPFS/NTFS/exFAT
/dev/sda2       142608384   149948415     3670016    7  HPFS/NTFS/exFAT
/dev/sda3       178259968   234440703    28090368   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x943416a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1852860415   926429184    7  HPFS/NTFS/exFAT
/dev/sdb2   *  1852860416  1892859903    19999744   83  Linux
/dev/sdb3      1892859904  1908860927     8000512   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x886a559e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1817208831   908603392   83  Linux
/dev/sdc2   *  18172
```

---

### Post by AmagicalFishy on 2014-04-13
Ah, neat. My fdisk commands seem to print things oppositely:
```
Disk /dev/sda: 7803 MB, 7803174912 bytes241 heads, 62 sectors/track, 1019 cylinders, total 15240576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f17ff


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          62    15225897     7612918    c  W95 FAT32 (LBA)
```


I also get: 
```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda1

Command (m for help): x


Expert command (m for help): v
Partition 1: previous sectors -637597257 disagrees with total 11717420
Partition 2: previous sectors 930513678 disagrees with total 3928898
Warning: partition 1 overlaps partition 2.
Partition 3: previous sectors -1 disagrees with total 152426
Total allocated sectors 2000982054 greater than the maximum 15225836


Expert command (m for help): 

```
If that helps any.

Anyone have any suggestions?

---

### Post by Mark Phelps on 2014-04-13
Another approach would be to use an MS Windows partitioning tool and see what it sees ... To do that, download and burn a CD of the Minitool Partition Wizard Boot CD.  Boot from that and see what it recognizes on the drive.  If it doesn't display useful partition info, my guess would be that your hard drive is failing.

---

### Post by AmagicalFishy on 2014-04-13
I'm also reluctantly coming to the conclusion that it's dead; there isn't a single program (other than the vague stuff I showed above) that recognizes that a hard drive is installed. I don't have a blank CD, unfortunately, but I will try to use another USB and boot it from that.

****, though. This computer's only like 1.5 years old and I treat it like it were my child.

The only thing giving me hope is are the /dev/sda1p1, /dev/sda1p2, /dev/sda1p3, and /dev/sda1p4 devices when I type "sudo fdisk -l /dev/sda1/". What are they and why would they be there if it were impossible to see my SSD (which I've erroneously been calling an HDD this whole thread). There's only one partition on this USB and it contains the Ubuntu I'm using to access this.

I'm going to try something that I should have tried before; I'm going to take out the SSD and boot back into this, then see if those devices still show up.

---

### Post by AmagicalFishy on 2014-04-13
Ah, same thing; what shows up is independent of whether or not the SSD is in.

Guess it's dead. D: Thanks for the help, though, guys.

---

### Post by 3rdalbum on 2014-04-14
WAIT. I had something similar happen to me. I worked out it was the SATA cable at fault. I had it twisted a bit too much when routing it through my computer case, and it had broken inside. Replacing the cable fixed everything. Try that before putting the SSD in the bin.

If the SSD is definitely dead, it should have a warranty. I think they are sometimes 3-5 years warranty, so investigate that.

---

