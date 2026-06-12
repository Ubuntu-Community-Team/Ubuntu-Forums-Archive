---
title: "GPT Disk error"
date: 2014-03-23
forum: General Help
---

### Post by meems on 2014-03-23
[COLOR=#222222]Plugged my external HDD in today to find it unmountable[/COLOR]

[COLOR=#222222]It's a 3TB HDD[/COLOR]

fdisk -l /dev/sde
```
Disk /dev/sde: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb993279
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1  4294967295  2147483647+  ee  GPT

```

lshw -C disk
```
 
  *-disk:0
       description: ATA Disk
       product: SAMSUNG HM321HI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 2AJ1
       serial: S24PJ9BB211562
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000aa26a
  *-disk:1
       description: ATA Disk
       product: SAMSUNG HD203WI
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 1AN1
       serial: S1UYJ1KZ309313
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=26ff1d3c-4adf-4247-8320-c252ad3b9aea
  *-disk:2
       description: ATA Disk
       product: ST33000651AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sde
       version: CC43
       serial: 9XK0945H
       size: 2794GiB (3TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=eb993279

```

sfdisk -d /dev/sde
```
# partition table of /dev/sde
unit: sectors/dev/sde1 : start=        1, size=4294967295, Id=ee
/dev/sde2 : start=        0, size=        0, Id= 0
/dev/sde3 : start=        0, size=        0, Id= 0
/dev/sde4 : start=        0, size=        0, Id= 0

```

mount /dev/sde1 usb
mount: /dev/sde1 is not a block device
```
root@kaj:/media# ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 Mar 23 13:36 /dev/sda
brw-rw---- 1 root disk 8,  1 Mar 23 12:33 /dev/sda1
brw-rw---- 1 root disk 8,  2 Mar 23 12:33 /dev/sda2
brw-rw---- 1 root disk 8,  3 Mar 23 12:33 /dev/sda3
brw-rw---- 1 root disk 8,  4 Mar 23 12:33 /dev/sda4
brw-rw---- 1 root disk 8,  5 Mar 23 12:33 /dev/sda5
brw-rw---- 1 root disk 8,  6 Mar 23 12:33 /dev/sda6
brw-rw---- 1 root disk 8, 16 Mar 23 13:36 /dev/sdb
brw-rw---- 1 root disk 8, 17 Mar 23 12:33 /dev/sdb1
brw-rw---- 1 root disk 8, 32 Mar 23 13:36 /dev/sdc
brw-rw---- 1 root disk 8, 33 Mar 23 12:33 /dev/sdc1
brw-rw---- 1 root disk 8, 48 Mar 23 14:19 /dev/sdd
brw-rw---- 1 root disk 8, 64 Mar 23 14:40 /dev/sde
cr-------- 1 root root 8, 65 Mar 23 14:45 /dev/sde1

```

fixparts /dev/sde
```
FixParts 0.8.1
Loading MBR data from /dev/sde
This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!
Exiting!
```

 
 gdisk /dev/sde
```
GPT fdisk (gdisk) version 0.8.1
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: not present
Creating new GPT entries.

```

gdisk p
```

Command (? for help): p
Disk /dev/sde: 5860533168 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): C2CBE4FD-2F47-4BBB-BB2E-630ECF4DFAEE
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 5860533101 sectors (2.7 TiB)
Number  Start (sector)    End (sector)  Size       Code  Name
Command (? for help):


```

fsck /dev/sde
```
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sde
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;

``` 
It's an NTFS partition... sadly I care very much about the data, so formatting isn't an option.

Any help/suggestions greatly appreciated

---

### Post by skibum3027 on 2014-03-23
It looks like your GPT table is missing/corrupt. I went through this a couple weeks ago with a GPT NTFS partition, so I might be able to help. I did manage to recover the data, but I never got gdisk to successfully create a partition table for an NTFS partition. I couldn't find a linux based solution at all. 

After about a week of pulling out my hair trying, I bought Active Partition Recovery for Windows. It found the partition and recreated the table in a couple clicks, problem solved. I believe there's a trial version you could download and see if it can find the partition(s) on the drive before you pay for it. 

FWIW, before you decide buying software is outlandish and there has to be an open source way to fix it; I thought the same thing. But, I wish I had just bought it upfront and saved myself the week of work trying to do it for free. Not only was the week's worth of time worth more than 50 bucks, 50 bucks to get all my data back seems like a steal in hindsight.

---

### Post by meems on 2014-03-23
When I boot into Windows (drive only visible inside computer management-Disk Management) it shows as a 700 or 800GB drive

Don't mind paying for software if it will do the job... should the size discrepancy concern me however?

---

### Post by skibum3027 on 2014-03-23
Inside windows Disk Management, it's just reading from the current GPT table, so no the discrepancy shouldn't concern you yet. Unless you've already formatted over that space, the data is most likely still there. Partition Recovery helps recover partitions from corrupt or missing tables by analyzing the disk instead of reading the table.

[http://www.partition-recovery.com/](http://www.partition-recovery.com/)

I recommend trying the demo to see if it recognizes your data before you buy it.

---

### Post by oldfred on 2014-03-23
Do not use fdisk on gpt drive. That (currently) is only for MBR(msdos) partitioned drives. You gpt drive has a protective MBR just so fdisk and other old tools do not damage a gpt drive and it should only have the one entry in the protective MBR partition table that says gpt.
But then you should have a gpt partition table and a backup partition table.

When you open gdisk as you did that is to create new partition table entries.
Does this show anything?
 sudo gdisk -l /dev/sda

      
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by meems on 2014-03-24
So I wanted to update you incase it indicates what the problem is/was for other people, the truth is, I don't know what happened.

I initially suspected my caddy (it's a seagate goflex) so I plugged the disk into my generic disk caddy (using eSata)
My windows PC doesn't have eSata, so I reverted back to USB (using my generic caddy).
In the meantime I started moving random data off old HDDs onto my raided setup (so the caddy was in use), so at the point of plugging it back into Windows to test/buy that program, the only caddy I had available was the original (seagate goflex). Low and behold, the disk appeared and there was my data.

Obviously the original caddy was where I started in the first place... I can't see how the above commands would have changed anything.
Am now in the process of getting all the data off it....

---

