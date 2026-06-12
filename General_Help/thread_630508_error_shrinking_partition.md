---
title: "error shrinking partition"
date: 2007-12-03
forum: General Help
---

### Post by KingWilliam on 2007-12-03
Hi,

Earlier I have shrunk my windows partition to install ubuntu on a new partition, Today I want to make the ntfs partition even smaller to create more space to be able to expand my ext3, But when i try to, I get an error, this is the info provided by GParted,

GParted 0.3.3

Libparted 1.7.1

Move /dev/sda1 to the left and shrink it from 63.47 GiB to 58.59 GiB    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 133114589
size: 133114527 (63.47 GiB)
calculate new size and position of /dev/sda1  00:00    ( SUCCES )
     	
requested start: 0
requested end: 122881184
requested size: 122881185 (58.59 GiB)
new start: 63
new end: 122881184
new size: 122881122 (58.59 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:10    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 68154630656 bytes (68155 MB)
Current device size: 68154637824 bytes (68155 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 61556 MB (90.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 62968 MB 0
Multi-Record : 68146 MB 1133
$MFTMirr : 45301 MB 1
Compressed : 68146 MB 75192
Sparse : 51504 MB 139989
Ordinary : 68155 MB 98738
You might resize at 61555826688 bytes or 61556 MB (freeing 6599 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem    ( ERROR )
     	
run simulation    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 62915134463 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 68154630656 bytes (68155 MB)
Current device size: 68154637824 bytes (68155 MB)
New volume size : 62915129856 bytes (62916 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 61556 MB (90.3%)
Collecting resizing constraints ...
Needed relocations : 1214409 (4975 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1064 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:10    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 68154630656 bytes (68155 MB)
Current device size: 68154637824 bytes (68155 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 61556 MB (90.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 62968 MB 0
Multi-Record : 68146 MB 1133
$MFTMirr : 45301 MB 1
Compressed : 68146 MB 75192
Sparse : 51504 MB 139989
Ordinary : 68155 MB 98738
You might resize at 61555826688 bytes or 61556 MB (freeing 6599 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:00    ( SUCCES )
     	
run simulation  00:00    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 68154630656 bytes (68155 MB)
Current device size: 68154637824 bytes (68155 MB)
New volume size : 68154630656 bytes (68155 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:00    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 68154630656 bytes (68155 MB)
Current device size: 68154637824 bytes (68155 MB)
New volume size : 68154630656 bytes (68155 MB)
Nothing to do: NTFS volume size is already OK.

========================================


Hope you guys can help,,,

thx

---

### Post by metalheart on 2007-12-03
ERROR: Extended record needed (1064 > 1024), not yet supported!
Please try to free less space.

---

### Post by Jose Catre-Vandis on 2007-12-03
Are you doing this with live cd or from within your ubuntu install? If the latter, try with live cd or Gparted or Parted Magic live cds. i have always found trying to sort out partitions from within Ubuntu problematic, but problem-free with the live cd approach

---

### Post by atlfalcons866 on 2007-12-03
is this a vista partition? if it use windows vista to resize ntfs,

---

### Post by KingWilliam on 2007-12-03
It is the vista partition I want to resize indeed. And I am running GParted from the 7.10 LiveCD. I once resized my same vista-partition with a higher amount, and that worked. So I don't think I am tryin to resize a to big chunk do I?

plz help :'( I cant install any software anymore...

---

### Post by Jose Catre-Vandis on 2007-12-03
> **atlfalcons866 said:**
> is this a vista partition? if it use windows vista to resize ntfs,

Yep, if Vista, use Vista Disk Manager, anything else WILL cause problems

---

### Post by atlfalcons866 on 2007-12-03
seems NTFS wants everything done windows.

---

### Post by KingWilliam on 2007-12-04
But I have been able to shrink the partition using GParted once. Why can't I use it again? :( If I use the Vista Disk manager, I cant free as much space due to the fact that the pagefile is on the drive to shrink.

---

### Post by Jose Catre-Vandis on 2007-12-07
Can you delete the page file in Vista, like you can do in Windows? In any case the pagefile would still be there even if you used Gparted, unless you are deleting it on exit?

Alternately you could move the pagefile (temporarily) to a different partition, but you are going to need some space for the pagefile in any case.

---

### Post by lvleph on 2007-12-07
> Needed relocations : 1214409 (4975 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...

That is your problem. You have a dirty drive. Log into windows
```
windows+r>>cmd>>chkdsk /r
```

BTW I had this exact problem yesterday. As long as you are not moving a Windows OS Partition GParted will work just fine. Once, you move a Windows OS Partition, you will have problems. Did that last week on my wife's computer.

---

### Post by Jose Catre-Vandis on 2007-12-08
I would issue a word of caution about just using Gparted with Vista. it doesn't always work for everyone, although i have had success when doing a dual boot install of mythbuntu over vista

[http://www.ubuntuforums.org/showthread.php?p=2353114#post2353114](http://www.ubuntuforums.org/showthread.php?p=2353114#post2353114)

---

### Post by KingWilliam on 2008-01-04
Gparted has done the trick. I worked a little longer with the amount of space I had untill i could shrink my Windows partition more. Shrinking it with a larger amount at once seemed to work. It can be that something else was wrong, which has been solved without me knowing in the time i was waiting to try again.

thx anyway to all of you ;)

---

