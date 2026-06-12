---
title: "Partition Editor"
date: 2008-07-02
forum: General Help
---

### Post by s3a on 2008-07-02
Why is it not shrinking my partition?! I tried with free space before and after; here are the results (saved details) of after:
[B]
[I]GParted 0.3.5

Libparted 1.7.1

Move /dev/sda1 to the left and shrink it from 70.31 GiB to 68.60 GiB  00:38    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 147444569
size: 147444507 (70.31 GiB)
calculate new size and position of /dev/sda1  00:00    ( SUCCES )
     	
requested start: 0
requested end: 143862074
requested size: 143862075 (68.60 GiB)
new start: 63
new end: 143862074
new size: 143862012 (68.60 GiB)
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:10    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 75491582464 bytes (75492 MB)
Current device size: 75491587584 bytes (75492 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use : 69409 MB (91.9%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 74118 MB 0
Multi-Record : 75492 MB 10840
$MFTMirr : 40975 MB 1
Compressed : 75385 MB 68601
Sparse : 66627 MB 25153
Ordinary : 75492 MB 25859
You might resize at 69408288768 bytes or 69409 MB (freeing 6083 MB).
Please make a test run using both the -n and -s options before real resizing!
shrink filesystem  00:16    ( ERROR )
     	
run simulation  00:16    ( ERROR )
     	
ntfsresize -P --force --force /dev/sda1 -s 73657350143 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 75491582464 bytes (75492 MB)
Current device size: 75491587584 bytes (75492 MB)
New volume size : 73657344512 bytes (73658 MB)
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use : 69409 MB (91.9%)
Collecting resizing constraints ...
Needed relocations : 354906 (1454 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
ERROR: Extended record needed (1032 > 1024), not yet supported!
Please try to free less space.
check filesystem on /dev/sda1 for errors and (if possible) fix them  00:11    ( SUCCES )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 75491582464 bytes (75492 MB)
Current device size: 75491587584 bytes (75492 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Found backup boot sector in the middle of the volume.
Space in use : 69409 MB (91.9%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature Last used at By inode
$MFT : 74118 MB 0
Multi-Record : 75492 MB 10840
$MFTMirr : 40975 MB 1
Compressed : 75385 MB 68601
Sparse : 66627 MB 25153
Ordinary : 75492 MB 25859
You might resize at 69408288768 bytes or 69409 MB (freeing 6083 MB).
Please make a test run using both the -n and -s options before real resizing!
grow filesystem to fill the partition  00:01    ( SUCCES )
     	
run simulation  00:00    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1 --no-action
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 75491582464 bytes (75492 MB)
Current device size: 75491587584 bytes (75492 MB)
New volume size : 75491582464 bytes (75492 MB)
Nothing to do: NTFS volume size is already OK.
real resize  00:01    ( SUCCES )
     	
ntfsresize -P --force --force /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 75491582464 bytes (75492 MB)
Current device size: 75491587584 bytes (75492 MB)
New volume size : 75491582464 bytes (75492 MB)
Nothing to do: NTFS volume size is already OK.

========================================[/I][/B]

When I choose to resize another partition, I also get a problem!

---

