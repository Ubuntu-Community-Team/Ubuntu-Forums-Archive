---
title: "Need help recovering files from SSD (mistakenly replaced partition table with gparted"
date: 2015-03-27
forum: General Help
---

### Post by naruto_uzumaki2 on 2015-03-27
I had windows installed on an SSD, but mistakenly created a new partition table on it using gparted.

Is there any way to at least recover some of the files?


What I have tried so far, is using testdisk, and the quick scan returns this


Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63


The harddisk (256 GB / 238 GiB) seems too small! (< 415 GB / 386 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors

  HPFS - NTFS          16044 163 56 47161 195 27  499896593

   HPFS - NTFS          19399  85 15 50516 116 49  499896593



The drive is a 256GB SSD


 There are files that I woud like to recover as they had not been backed up.



-------------------------------------------------------------------------------------------------------------


 after it lists what it can't recover, it goes to this window
 (but it detects the partition as 111 GiB)
when the drive originally has a 100MB partition, and an additional partition (drive C) taking the rest of the space on the drive.


Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63

     Partition               Start        End    Size in sectors

* HPFS - NTFS              0   1  1 14592 254 63  234436482



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continueubuntu-gnome@ubuntu-gnome:~$ 
NTFS, blocksize=4096, 120 GB / 111 GiB





-------------------------------------------------------------------------------------------------



A deeper scan shows 

Disk /dev/sda - 256 GB / 238 GiB - CHS 31130 255 63

     Partition               Start        End    Size in sectors

   HPFS - NTFS              0   1  1 14592 254 63  234436482

   HPFS - NTFS              0  32 33    12 223 19     204800 [Data]

   HPFS - NTFS              0  32 33 31130 190 36  500113408

>  HPFS - NTFS             12 223 20 31130  28  2  499898368


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, blocksize=4096, 255 GB / 238 GiB


with the last partition showing the correct size, but I am not sure how to select it or if it is even good.



===============================

Edit: I am also imaging the drive using ddrescue at the moment. Is there a way to perform data recovery on the image file in order to reduce the risk of data loss on the SSD?

---

### Post by naruto_uzumaki2 on 2015-03-27
Wanted to add, I tried a tool called "photorec" seems to come with testdisk, and it is able to recover files, but has no entry for file formats such as docx.

Is there any tool that will let me browse the recoverable files?

---

### Post by oldfred on 2015-03-27
I do not have Windows, but some users that do have posted these:

 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by Mark Phelps on 2015-03-27
As oldfred has already mentioned, it's best to use Windows data recovery apps to recover lost Windows files and folders.

---

