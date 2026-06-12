---
title: "Please help to rescue ext4 partition with important files"
date: 2013-08-06
forum: General Help
---

### Post by jon10 on 2013-08-06
Yes I know I should have a backup!

I moved my computer today (physically picked it up) and when I powered back on one of my HDDs failed to mount. I since discovered that it was due to a faulty partition table. The disk was a primary ext4 partition that used the entire disk (2TB)

I started out by using testdisk. A quick search did not find the partition but once I started a deeper search it came up straight away. Only problem was that after the search finished, the partition was not shown in the final partition table and I was not able to write or recover it. I now have the start/end of the partition from testdisk. Can I just add a new partition with this start/end and have everything come back or does it not work like this? UPDATE: The start and stop that I have from testdisk seem to be outside the range of the disk.  Start is 0,0,1 End is 243201,80,63 with total size of 3907029168. The disk total size is 3907029105.

I tried editing the partition table so that it is now this:
```
 
[FONT=arial]# partition table of /dev/sdb[/FONT]
[FONT=arial]unit: sectors[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]/dev/sdb1 : start=        1, size=3907029105, Id=83[/FONT]
[FONT=arial]/dev/sdb2 : start=        0, size=        0, Id= 0[/FONT]
[FONT=arial]/dev/sdb3 : start=        0, size=        0, Id= 0[/FONT]
[FONT=arial]/dev/sdb4 : start=        0, size=        0, Id= 0[/FONT]

```

However this did not work and I still can't mount the disk. I tried checking the superblock backups using

```
mke2fs -n /dev/sdb1
```
and I get a message saying that "/dev/sdb1 alignment is off by 3584 bytes" - does this mean I have the start of the partition wrong? Or am I just going about this all wrong?

Thanks if you can help out.

Jon

---

### Post by oldfred on 2013-08-07
Testdisk still uses CHS - cylinders, heads, sectors and it has been known to round incorrectly. Occasionally it will write a new partition table that is larger than drive and we have to use fixparts to correct it.

You should have been able to copy the data from the deeper search with testdisk.

You can also use sfdisk (if MBR/msdos, not gpt) to write partition table:
 Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)


 this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit
else if it is not ok
then post the output of option p and v

Also:

 GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

      
 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)

Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

