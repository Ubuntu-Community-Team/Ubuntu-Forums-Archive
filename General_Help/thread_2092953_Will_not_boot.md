---
title: "Will not boot"
date: 2012-12-09
forum: General Help
---

### Post by labibij on 2012-12-09
I am dual booting windows 8 and Ubuntu using Wubi. I tried to resize the partition for them in order to make a third partition, but now, Windows won't boot and Ubuntu gives me a limited Grub command line. I have tried checking the partition with gParted on an Ubuntu Live CD and have gotten the following details:


GParted 0.11.0 --enable-libparted-dmraid
 Libparted 2.3
    **Check and repair file system (ntfs) on /dev/sda2**  00:00:09    ( ERROR )             calibrate /dev/sda2  00:00:00    ( SUCCESS )             [I]path: /dev/sda2
start: 206,848
end: 976,771,071
size: 976,564,224 (465.66 GiB)[/I]          check file system on /dev/sda2 for errors and (if possible) fix them  00:00:09    ( ERROR )             ***ntfsresize -P -i -f -v /dev/sda2***             [I]ntfsresize v2012.1.15AR.1 (libntfs-3g)
Device name        : /dev/sda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 500000879104 bytes (500001 MB)
Current device size: 500000882688 bytes (500001 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 3914085 (0x3bb965): extra cluster in $Bitmap
Cluster accounting failed at 3914086 (0x3bb966): extra cluster in $Bitmap
Cluster accounting failed at 3914087 (0x3bb967): extra cluster in $Bitmap
Cluster accounting failed at 3914088 (0x3bb968): extra cluster in $Bitmap
Cluster accounting failed at 3914089 (0x3bb969): extra cluster in $Bitmap
Cluster accounting failed at 3914090 (0x3bb96a): extra cluster in $Bitmap
Cluster accounting failed at 3914091 (0x3bb96b): extra cluster in $Bitmap
Cluster accounting failed at 3914092 (0x3bb96c): extra cluster in $Bitmap
Cluster accounting failed at 3914093 (0x3bb96d): extra cluster in $Bitmap
Cluster accounting failed at 3914094 (0x3bb96e): extra cluster in $Bitmap
Cluster accounting failed at 3914095 (0x3bb96f): extra cluster in $Bitmap
Cluster accounting failed at 3914096 (0x3bb970): extra cluster in $Bitmap
Cluster accounting failed at 3914097 (0x3bb971): extra cluster in $Bitmap
Cluster accounting failed at 3914098 (0x3bb972): extra cluster in $Bitmap
Cluster accounting failed at 3914099 (0x3bb973): extra cluster in $Bitmap
Cluster accounting failed at 3914100 (0x3bb974): extra cluster in $Bitmap
Cluster accounting failed at 3914101 (0x3bb975): extra cluster in $Bitmap
Cluster accounting failed at 3914102 (0x3bb976): extra cluster in $Bitmap
Cluster accounting failed at 3914103 (0x3bb977): extra cluster in $Bitmap
Cluster accounting failed at 3914104 (0x3bb978): extra cluster in $Bitmap
Cluster accounting failed at 3914105 (0x3bb979): extra cluster in $Bitmap
Cluster accounting failed at 3914106 (0x3bb97a): extra cluster in $Bitmap
Cluster accounting failed at 3914107 (0x3bb97b): extra cluster in $Bitmap
Cluster accounting failed at 3914108 (0x3bb97c): extra cluster in $Bitmap
Cluster accounting failed at 3914109 (0x3bb97d): extra cluster in $Bitmap
Cluster accounting failed at 3914110 (0x3bb97e): extra cluster in $Bitmap
Cluster accounting failed at 3914111 (0x3bb97f): extra cluster in $Bitmap
Cluster accounting failed at 3914112 (0x3bb980): extra cluster in $Bitmap
Cluster accounting failed at 3914113 (0x3bb981): extra cluster in $Bitmap
Cluster accounting failed at 3914114 (0x3bb982): extra cluster in $Bitmap
Cluster accounting failed at 3914115 (0x3bb983): extra cluster in $Bitmap
Cluster accounting failed at 3914116 (0x3bb984): extra cluster in $Bitmap
Cluster accounting failed at 3914117 (0x3bb985): extra cluster in $Bitmap
Cluster accounting failed at 3914118 (0x3bb986): extra cluster in $Bitmap
Cluster accounting failed at 3914119 (0x3bb987): extra cluster in $Bitmap
Cluster accounting failed at 3914120 (0x3bb988): extra cluster in $Bitmap
Cluster accounting failed at 3914121 (0x3bb989): extra cluster in $Bitmap
Cluster accounting failed at 3914122 (0x3bb98a): extra cluster in $Bitmap
Cluster accounting failed at 3914123 (0x3bb98b): extra cluster in $Bitmap
Cluster accounting failed at 3914124 (0x3bb98c): extra cluster in $Bitmap
Cluster accounting failed at 3914125 (0x3bb98d): extra cluster in $Bitmap
Cluster accounting failed at 3914126 (0x3bb98e): extra cluster in $Bitmap
Cluster accounting failed at 3914127 (0x3bb98f): extra cluster in $Bitmap
Cluster accounting failed at 3914128 (0x3bb990): extra cluster in $Bitmap
Cluster accounting failed at 3914129 (0x3bb991): extra cluster in $Bitmap
Cluster accounting failed at 3914130 (0x3bb992): extra cluster in $Bitmap
Cluster accounting failed at 3914131 (0x3bb993): extra cluster in $Bitmap
Cluster accounting failed at 3914132 (0x3bb994): extra cluster in $Bitmap
Cluster accounting failed at 3914133 (0x3bb995): extra cluster in $Bitmap
Cluster accounting failed at 3914134 (0x3bb996): extra cluster in $Bitmap
Cluster accounting failed at 3914135 (0x3bb997): extra cluster in $Bitmap
Cluster accounting failed at 3914136 (0x3bb998): extra cluster in $Bitmap
Cluster accounting failed at 3914137 (0x3bb999): extra cluster in $Bitmap
Cluster accounting failed at 3914138 (0x3bb99a): extra cluster in $Bitmap
Cluster accounting failed at 3914139 (0x3bb99b): extra cluster in $Bitmap
Cluster accounting failed at 3914140 (0x3bb99c): extra cluster in $Bitmap
Cluster accounting failed at 3914141 (0x3bb99d): extra cluster in $Bitmap
Cluster accounting failed at 3914142 (0x3bb99e): extra cluster in $Bitmap
Cluster accounting failed at 3914143 (0x3bb99f): extra cluster in $Bitmap
Cluster accounting failed at 3914144 (0x3bb9a0): extra cluster in $Bitmap
Cluster accounting failed at 3914145 (0x3bb9a1): extra cluster in $Bitmap
Cluster accounting failed at 3914146 (0x3bb9a2): extra cluster in $Bitmap
Cluster accounting failed at 3914147 (0x3bb9a3): extra cluster in $Bitmap
Cluster accounting failed at 3914148 (0x3bb9a4): extra cluster in $Bitmap
Filesystem check failed! Totally 64 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.
[/I]             ========================================
  
When I boot windows, I get the windows or Ubuntu menu. If I go to other options and open a limited command prompt in windows, I try chkdsk /f as above, but I get an error that the disk is write protected. I had given it full write permission and tried everything again, and it still wouldn't work.

---

### Post by oldfred on 2012-12-09
Welcome to the forums. 

I do not know wubi, but I thought it did not work with Windows 8 nor gpt partitioned drives. 

Also Windows 8 is always hibernated unless you turned that off, so all repairs should just be done from Windows.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Bucky Ball on 2012-12-09
Just a note: a Wubi install is _*not*_ a dual-boot, it is Wubi installed in Windows. A dual-boot is Windows and Ubuntu on two separate partitions and totally independent of each other ...

Wubi is intended as a 'try before you install' option and is not a permanent solution. Consequently, many of us here don't actually know much about Wubi ...

---

