---
title: "PLEASE HELP - RAID array missing after clonezilla backup"
date: 2016-02-06
forum: General Help
---

### Post by XBNCPRk on 2016-02-06
Quick system specs - 
14.04 with latest kernel (I think -60?) and everything else up to date. 
SSD boot drive with nothing but the os, 8x4tb RAID6 array, with one ext4 partiton (~24tb). 

System was running fine earlier in the day, so turned it off, booted up to a live usb of clonezilla to make a monthly backup image of the boot drive, got a message that said the free block count was incorrect on sda (the ssd drive), and it aborted the image. I reran clonezilla including its fsck options, it adjusted the free block count and it completed with no other error messages. Shut down the computer, unplugged the external backup drive and live usb, restarted, and my raid array is totally missing in action. Mdadm says it finds 1 of the 8 drives for the array, and thus cannot start it. Disks shows the other drives all as a mix of ext3/ext4/unknown, some bootable some not (none should be), some raid array members some not (all should be)... Booting to a live usb of ubuntu also shows the same thing, with mdadm unable to find the array using the --assemble --scan command.

I unfortunately cant go backwards to a prior month backup image since the new larger array was created in the interim. Im not overly concerned about the os drive since I can rebuild that in a couple hours and I am virtually certain that the data on the drives is still intact and in place since clonezilla only took 2-3 mins to run, and to do anything with ~20tb of data takes literally days. Is there a way to recover or recreate the partition tables on the individual drives without losing the data on them?

---

