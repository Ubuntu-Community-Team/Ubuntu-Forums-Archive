---
title: "Issue with 2nd hard drive on read only"
date: 2019-10-15
forum: General Help
---

### Post by granderzander on 2019-10-15
Hi i am pretty new with Ubuntu, i'm having trouble with a 2tb Seagate hard drive that i have partitioned and mounted. I cannot figure out why the hard drive is read only and when i try to download something it says it isn't writable. I use Ubuntu 18.04, I'm not sure what information anyone needs to correct this but I have not had this problem with any other hard drive and i am happy to provide information needed.

---

### Post by TheFu on 2019-10-15
Well, usually when a partition's file system (not a drive), goes read-only, it is because of corruption and the file system is protecting itself against more issues.
The corruption can be logical or physical.  Seagate HDDs between 750G-7TB have a poor reliability history compared to almost any other vendor.  8, 10, 12TB Seagate HDDs have excellent reliability, so they do appear to have addresses the issues.

Please don't confuse a "drive" with a partition.  Windows uses the terms interchangeably, but that is incorrect.  Every other OS cares and I will be specific about one or the other.

So, the answers that would be most helpful to us are:
* which file system is causing issues. Common choices are ext4, ext3, ZFS, NTFS, exFAT.  The file system matters.
* please show the partitioning information.  **sudo fdisk -l** will show it.  Use "code tags" in the Advanced editor here. Copy/paste the command AND the output.  Please, then wrap in code tags so everything lines up just like it did in the terminal.
* SMART is a built-in health capture system that all storage devices support.  You'll need to find a tutorial on using smartctl and follow it.  Install the package, run a test on the **drive**, run a report, then post the report using 'code tags' so everything lines up.  I need to see the raw numbers. The testing and report are for the disk, not a partition.

If you don't use *code tags* when posting, the data it just too hard to read.

---

### Post by granderzander on 2019-10-16
```
sudo fdisk -l
[sudo] password for zander: 
Disk /dev/loop0: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 54.5 MiB, 57151488 bytes, 111624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 54.5 MiB, 57139200 bytes, 111600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 3.7 MiB, 3821568 bytes, 7464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 140.7 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4df821c2

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 234440703 234438656 111.8G 83 Linux


Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 7C37542E-2B88-4D55-88A1-578782E78BBB

Device     Start        End    Sectors  Size Type
/dev/sdb1     34 3907029134 3907029101  1.8T Linux filesystem

Partition 1 does not start on physical sector boundary.


Disk /dev/loop8: 44.2 MiB, 46325760 bytes, 90480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 149.9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 3.7 MiB, 3821568 bytes, 7464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 4.2 MiB, 4403200 bytes, 8600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 956 KiB, 978944 bytes, 1912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 149.9 MiB, 157192192 bytes, 307016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 140.7 MiB, 147501056 bytes, 288088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 89 MiB, 93327360 bytes, 182280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 89.1 MiB, 93454336 bytes, 182528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

I can't get smart tools to work at all it just tells me this  "Please select the mail server configuration type that best meets your     
  &#9474; needs."  however i cannot interact with terminal at all after that and i can't select anything.

---

### Post by granderzander on 2019-10-16
```
 sudo ntfsfix /dev/sdb
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.


```

I checked if the hard drive is ntfs and this came up. Is it possibly faulty?

---

### Post by granderzander on 2019-10-16
I solved the issue it was all just me being stupid

---

### Post by QIII on 2019-10-16
Would you care to share the solution and help the next person out?

---

