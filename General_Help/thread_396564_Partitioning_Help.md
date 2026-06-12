---
title: "Partitioning Help"
date: 2007-03-29
forum: General Help
---

### Post by ShellsOnTheFloor on 2007-03-29
I am currently on a dual-boot system with Ubuntu and Windows XP. I primarily use Ubuntu, with Windows only staying so I can play some games and keep fresh on how to use it when I'm helping people with computer problems.

I have three partitions on my hard drive. One is Extended, with logical partitions for Ubuntu and Swap Space. The second is for Windows XP, and the third is for a shard Fat32 partition.

I'm trying to make a fourth partition out of extra space on the Windows XP partition. I first tried GParted, but it didn't work. I saved the details, and they are at the end of this post.

PartitionMagic doesn't work either, giving me an Error 1529. I've tried a SystemRescue Gentoo Live CD with GParted installed, but that didn't work either. Does anyone know what's going on?

GParted 0.2.5

Resize /dev/hda2 from 102.51 GiB to 92.75 GiB    ( ERROR )
     	
check filesystem on /dev/hda2 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/hda2
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/hda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 110070690304 bytes (110071 MB)
Current device size: 110070696960 bytes (110071 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 38897 MB (35.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 22086 MB 0
Multi-Record : 60542 MB 2383
$MFTMirr : 7342 MB 1
Compressed : 61297 MB 43925
Ordinary : 61480 MB 20072
You might resize at 38896050176 bytes or 38897 MB (freeing 71174 MB).
Please make a test run using both the -n and -s options before real resizing!
resize the filesystem    ( ERROR )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/hda2 -s 99577135104 --no-action
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/hda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 110070690304 bytes (110071 MB)
Current device size: 110070696960 bytes (110071 MB)
New volume size : 99577131520 bytes (99578 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 38897 MB (35.3%)
Collecting resizing constraints ...
Needed relocations : 0 (0 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
resize the filesystem    ( ERROR )
     	
ntfsresize -P --force --force /dev/hda2 -s 99577135104
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
ERROR(95): Opening '/dev/hda2' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.
check filesystem on /dev/hda2 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/hda2
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/hda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 110070690304 bytes (110071 MB)
Current device size: 110070696960 bytes (110071 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 38897 MB (35.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 22086 MB 0
Multi-Record : 60542 MB 2383
$MFTMirr : 7342 MB 1
Compressed : 61297 MB 43925
Ordinary : 61480 MB 20072
You might resize at 38896050176 bytes or 38897 MB (freeing 71174 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition    ( ERROR )
     	
run simulation    ( SUCCES )
     	
ntfsresize -P --force --force /dev/hda2 --no-action
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Device name : /dev/hda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 110070690304 bytes (110071 MB)
Current device size: 110070696960 bytes (110071 MB)
New volume size : 110070690304 bytes (110071 MB)
Nothing to do: NTFS volume size is already OK.
grow filesystem to fill the partition    ( ERROR )
     	
ntfsresize -P --force --force /dev/hda2
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
ERROR(95): Opening '/dev/hda2' as NTFS failed: Operation not supported
The NTFS journal file is unclean. Please shutdown Windows properly before
using this software! Note, if you have run chkdsk previously then boot
Windows again which will automatically initialize the journal correctly.
check filesystem on /dev/hda2 for errors and (if possible) fix them    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/hda2
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/hda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 110070690304 bytes (110071 MB)
Current device size: 110070696960 bytes (110071 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use : 38897 MB (35.3%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 22086 MB 0
Multi-Record : 60542 MB 2383
$MFTMirr : 7342 MB 1
Compressed : 61297 MB 43925
Ordinary : 61480 MB 20072
You might resize at 38896050176 bytes or 38897 MB (freeing 71174 MB).
Please make a test run using both the -n and -s options before real resizing!

========================================

---

### Post by solar george on 2007-03-29
Try starting windows again, running the chkdsk program and then shutting down properly.

Then try partitioning again.

---

### Post by ShellsOnTheFloor on 2007-03-29
I'm sorry I forgot to mention it in the original post, but I've run chkdsk /f many many many times, and it hasn't worked yet.

---

