---
title: "Need to format a memory card"
date: 2012-10-18
forum: General Help
---

### Post by TimEnid on 2012-10-18
How can i format this card so that i have all of the 64gbs. Here is a screenshot of how its currently formatted. I am not sure how it got like this. But when i format it to exfat, fat 32 or ntfs, i only get 32gb available. Its a 64gb card. Any suggestions?

---

### Post by efflandt on 2012-10-18
You only have an extended and logical partition on it, which is fully formatted, but is only half of the memory.

I have never really understood the Disk Utility that Ubuntu uses.  One time when I thought I told it to mark a partition as the boot partition it just started churning endlessly (not sure what it was doing).

I would use **gparted** (install it if you have not).  Use that to delete the logical and extended partition and put a primary partition on it the full size of the memory.

Note that FAT32 would be accessible to most types of operating systems or devices, but is limited to 4 GB file size, the cluster size may not be real efficient (small files may consume more space than they actually occupy), and I think some operating systems may have a problem with FAT32 partitions larger than 32 GB each.  So ntfs might be best if it needs to be accessible to Windows.  If you have any devices that only do FAT, and not ntfs, you may want to use different memory for them, since they may not be able to handle that much in one partition anyway.

The largest memory I have is 32 GB SDHC, and I split that into 3 primary ext2 partitions, one for Lubuntu /, one for Ubuntu /, and one for a common /home, to boot Linux from the card slot of my tablet PC (its internal drive is 32 GB SSD w/Win7 Pro).

---

