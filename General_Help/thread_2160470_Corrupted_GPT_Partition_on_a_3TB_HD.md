---
title: "Corrupted GPT Partition on a 3TB HD"
date: 2013-07-07
forum: General Help
---

### Post by c.monty on 2013-07-07
Hello!

I'm hoping to get some support here in this forum for my problem.
Let me first describe what happened, and then the situation "as is".

I bought a 3TB HD WD30EZRX to use it as a storage for movie files recorded with my DVB-S (Vu+ Solo2). This device however cannot create partitions with GUID Partition Table (GPT), and therefore I connected the HD to my desktop running with linux. The mainboard of the desktop is Gigabyte GA-P35-DS4 (Rev. 1.0).
What I didn't know and therefore didn't consider: old mainboards (including the GA-P35-DS4) cannot identify HD > 2TB.

So, after booting the desktop I identified that the HD is only showing a capacity of 2TB.
```
knoppix@Microknoppix:~$ sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000421444608 bytes
255 heads, 63 sectors/track, 243204 cylinders, total 3907073134 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table
```

Checking the internet for this I found a simple solution: using GPT fdisk (gdisk) and creating a GPT partition table.
This worked fine, and finally a got a primary partition of size 3TB, that I formatted with XFS.
There was no issue mounting this new partition, and [FONT=Courier New]df -h[/FONT] confirmed that 3TB was available on this drive.
After this I started to store several recordings (ts-files) on the drive with a total size of approx. 2,4TB.
Still no indication for an issue, and I unmounted the drive from the desktop in order to connect it to the DVB-S device using eSATA.
The DVB-S device identified the disk immediatelly as a 3TB drive and I mounted it without issues. There were no issues with reading and writing of that drive.

Then, some days later I connected the disk back to my desktop, and suddenly I identified an error when mounting the disk. Checking with gdisk I got this output:
```
knoppix@Microknoppix:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.4

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

```

This error is identical to a posting [here]("http://ubuntuforums.org/showthread.php?t=1956173") in this forum.
I followed the steps described by Aritsugu to recover the data from the disk, means I used another disk WD30EZRX and copied the data to this new disk.
```
knoppix@Microknoppix:~$ dd_rescue -l ddlogfile /dev/sda /dev/sdb
dd_rescue: (warning): /dev/sda is a block device; -a not recommended; -A recommended
dd_rescue: (info) expect to copy 1953536567kB from /dev/sdb
dd_rescue: (info): read /dev/sdb (1953536567.0k): EOF
dd_rescue: (info): Summary for /dev/sdb -> /dev/sda:
dd_rescue: (info): ipos:1953536567.0k, opos:1953536567.0k, xferd:1953536567.0k
                   errs:      0, errxfer:         0.0k, succxfer:1953536567.0k
             +curr.rate:      164kB/s, avg.rate:   111752kB/s, avg.load:-11.9%
             >----------------------------------------.<  99%  ETA:  0:00:00 

```

The output shows no error, and I continued to fix the issues on the copy following the documentation of Aritsugu in [posting #13]("http://ubuntuforums.org/showthread.php?t=1956173&p=11838103#post11838103").
However, this didn't work and I still cannot mount the disk.

My conclusion is, that fixing the errors will not work unless I have a desktop that identifies the HD with its full capacity of 3TB.
However, I think it should be possible to recover 2TB of data using [FONT=Courier New]dd_rescue[/FONT].

Question:
What is the correct syntax to recover as much data from the source disk?
I assume the data recovery is only limited by the number of sectors?
If this is true, how must this be reflected in the syntax of the [FONT=Courier New]dd_rescue[/FONT] statement?

THX

---

### Post by oldfred on 2013-07-09
The author of gdisk has posted in this forum not to use dd with gpt partitions. The partition has internal data which should not be dd'd. I think a dd of the entire drive may work, but you end up with duplicate UUID and all the internal gpt structures so both drives then cannot be mounted at same time or conflicts will occur.

       Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
Do not use dd with gpt partitions. Whole drive ok if old drive not used anymore, or no duplicates.
But do not use dd for copies from MBR to gpt partitioned drives, can use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
Restore full drive dd backup - resync gpt partition tables and fsck pursuvant
[http://ubuntuforums.org/showthread.php?t=2145563](http://ubuntuforums.org/showthread.php?t=2145563)

---

