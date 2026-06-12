---
title: "Can't copy big files from XP to neutral drive"
date: 2007-07-18
forum: General Help
---

### Post by catnappist on 2007-07-18
A few days ago I re-installed Feisty after straightening up the partitions on my 80Gb drive. WinXP is first (still), /root and /home are second (ext3), with /swap in the third partition, just like it should have been in the first place and wasn't.  While I was at it, I rearranged partitions on my 250Gb catch-all-the-extra-crap and backup drive (all three partitions FAT32).  Feisty works fine, XP still works, except that when in Windows I can't copy large files to my practically empty big drive.  I get 'disk-is-full' errors even if I try to copy to an empty 100Gb partition.  :confused:

I'm thinking maybe I messed up a configuration file in Windows that was connected to something I forgot about and either moved or erased from the 250Gb drive, but I don't have a clue as to what I should look for.  I would appreciate any help.

---

### Post by NT4usB on 2007-07-18
How big is big? FAT32 has a 4 gig (file) limit.

---

### Post by catnappist on 2007-07-18
FAT16 has a 4Gb file limit.  My fourth partition on the 250Gb drive used to be FAT16, which I deleted and absorbed into the previous third partition.  I wonder if that could have anything to do with it?

---

### Post by NT4usB on 2007-07-18
*The maximum possible size for a file on a FAT32 volume is 4 GiB minus 1 Byte (232&#8722;1 bytes). For most users, this has become the most nagging limit of FAT32 as of 2007, since video capture and editing applications and some other software can easily exceed this limit. Most new Windows machines now ship with NTFS and thus avoid these problems, but until mid-2006, those who run dual boot systems or who move external data drives between computers with different operating systems had little choice but to stick with FAT32. Since then, full support for NTFS has become available in Linux and many other operating systems, by installing the FUSE library (on Linux) together with the NTFS-3G application. Data exchange is also possible between Windows and Linux by using the Linux-native ext2 or ext3 file systems through the use of external drivers for Windows, such as ext2 IFS; however, Windows cannot boot from ext2 or ext3 partitions.*

[http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)

---

### Post by steevols on 2007-07-18
I'd run chkdsk on the drive to check for bad headers... those have "filled" my drive before. Could be a bunny trail, or a quick fix.

---

### Post by catnappist on 2007-07-18
steevols, I only know how to do fdisk -l from linux.  Maybe you could give me something else I don't have to go into DOS for?

NT4usB, that's weird (and enlightening).  Gparted limited me to 4Gb when I was doing the partitioning (partitionizing?), but didn't when I was partitioning the other areas.  They really should work on that!  :o  So the drive would be compatible with Windoze and Linux if I formatted it in ext2 or ext3?

---

### Post by steevols on 2007-07-18
Well, boot to Windows, bring up a "cmd" from the run box, and then type "chkdsk [drive]"...

---

### Post by catnappist on 2007-07-18
I did (it was inevitable, huh?). :)

C:\>chkdsk d:
The type of the file system is FAT32.
Volume DEMANIAK created 7/15/2007 6:01 PM
Volume Serial Number is 469A-51D1
Windows is verifying files and folders...
File and folder verification is complete.
Windows has checked the file system and found no problems.
   78,110,000 KB total disk space.
           48 KB in 3 hidden files.
   78,109,936 KB are available.

       16,384 bytes in each allocation unit.
    4,881,875 total allocation units on disk.
    4,881,871 allocation units available on disk.

C:\>chkdsk e:
The type of the file system is FAT32.
Volume ETENKAK created 7/15/2007 6:01 PM
Volume Serial Number is 469A-51D2
Windows is verifying files and folders...
File and folder verification is complete.
Windows has checked the file system and found no problems.
   63,457,872 KB total disk space.
           48 KB in 3 hidden files.
   63,457,808 KB are available.

       16,384 bytes in each allocation unit.
    3,966,117 total allocation units on disk.
    3,966,113 allocation units available on disk.

C:\>chkdsk f:
The type of the file system is FAT32.
Volume FREZNOK created 7/12/2007 2:48 PM
Volume Serial Number is 4696-3E49
Windows is verifying files and folders...
File and folder verification is complete.
Windows has checked the file system and found no problems.
  102,508,848 KB total disk space.
          336 KB in 3 hidden files.
        2,608 KB in 161 folders.
   18,826,112 KB in 1,012 files.
   83,679,776 KB are available.

       16,384 bytes in each allocation unit.
    6,406,803 total allocation units on disk.
    5,229,986 allocation units available on disk.

Must be something else, eh?  'preciate the suggestion!

---

### Post by catnappist on 2007-07-18
Hey NT4usB, you still here?!

---

### Post by merlinus on 2007-07-18
Windows can read and write to ext2 and ext3 partitions via the ifs driver:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

-merlin

---

### Post by catnappist on 2007-07-18
So I noticed.  I formatted the first partition (formerly D drive) to ext3.  Neither Windoze nor Linux seems to like it now.  Any suggests?  I'm trying to find common ground for both systems!

---

### Post by catnappist on 2007-07-18
Crap.  Come to think of it, at one point I had two NTFS partitions on that drive before I decided to make the whole thing FAT32.  When I got rid of them, I think that's when I lost stuff that was bigger than 4Gb from the FAT32 partition (yeah, DVD ISOs!).  Since it was working that way, I think that's what I'll go back to.

Thanks all!

---

### Post by strabes on 2007-07-18
Just make the whole thing ext3. When you plug it in it should automagically mount in linux. Don't know about in XP because I only use XP for gaming and don't need access to my external when in XP.

---

