---
title: "gparted failed shrinking mac hfs+"
date: 2008-05-02
forum: General Help
---

### Post by kensuguro on 2008-05-02
I tried shrinking a hfs+ drive, and gparted failed half way.. I got the details file, and I was wondering if anyone could tell me if this is recoverable.. I know it finished the "reading" part of the process, but the "copy" part failed.  So, now I have 60Gb of what was 90..  

Last time I tried resizing, it failed a few times, leaving no permanent damage.. so unplugging and re-mounting put it back to normal.. this time it doesn't seem to be case.  Maybe it just boils down to back up everything before you try stuff?  (sigh)  I thought this thing was pretty solid, because of my last experience.

Anyway, here's what I got:

GParted 0.3.3

Libparted 1.7.1

Move /dev/sde3 to the left and shrink it from 141.93 GiB to 90.06 GiB  02:14:21    ( ERROR )
     	
calibrate /dev/sde3  00:00    ( SUCCES )
     	
path: /dev/sde3
start: 262208
end: 297901727
size: 297639520 (141.93 GiB)
calculate new size and position of /dev/sde3  00:00    ( SUCCES )
     	
requested start: 257040
requested end: 189133244
requested size: 188876205 (90.06 GiB)
new start: 257040
new end: 189133244
new size: 188876205 (90.06 GiB)
check filesystem on /dev/sde3 for errors and (if possible) fix them    ( N/A )
     	
checking is not available for this filesystem
shrink filesystem  56:34    ( SUCCES )
     	
using libparted
shrink partition from 141.93 GiB to 90.06 GiB  00:00    ( SUCCES )
     	
old start: 262208
old end: 297901727
old size: 297639520 (141.93 GiB)
new start: 262208
new end: 189138412
new size: 188876205 (90.06 GiB)
check filesystem on /dev/sde3 for errors and (if possible) fix them    ( N/A )
     	
checking is not available for this filesystem
grow filesystem to fill the partition    ( N/A )
     	
growing is not available for this filesystem
calculate new size and position of /dev/sde3  00:00    ( SUCCES )
     	
requested start: 257040
requested end: 189133244
requested size: 188876205 (90.06 GiB)
new start: 257040
new end: 189133244
new size: 188876205 (90.06 GiB)
check filesystem on /dev/sde3 for errors and (if possible) fix them    ( N/A )
     	
checking is not available for this filesystem
move partition to the left  00:00    ( SUCCES )
     	
old start: 262208
old end: 189138412
old size: 188876205 (90.06 GiB)
new start: 257040
new end: 189133244
new size: 188876205 (90.06 GiB)
move filesystem to the left    ( EXECUTING )
     	
perform readonly test  50:50    ( SUCCES )
     	
using internal algorithm
read 188876205 sectors
finding optimal blocksize
     	
read 32768 sectors using a blocksize of 128 sectors  00:01    ( SUCCES )
     	
32768 of 32768 read
0.731576 seconds
read 32768 sectors using a blocksize of 256 sectors  00:01    ( SUCCES )
     	
32768 of 32768 read
0.671348 seconds
read 32768 sectors using a blocksize of 512 sectors  00:00    ( SUCCES )
     	
32768 of 32768 read
0.643046 seconds
read 32768 sectors using a blocksize of 1024 sectors  00:01    ( SUCCES )
     	
32768 of 32768 read
0.60101 seconds
read 32768 sectors using a blocksize of 2048 sectors  00:00    ( SUCCES )
     	
32768 of 32768 read
0.610047 seconds
optimal blocksize is 1024 sectors (512.00 KiB)
read 188712365 sectors using a blocksize of 1024 sectors  50:47    ( SUCCES )
     	
188712365 of 188712365 read
188876205 sectors read
perform real move  26:56    ( ERROR )
     	
using internal algorithm
copy 188876205 sectors    ( ERROR )
finding optimal blocksize
     	
copy 32768 sectors using a blocksize of 64 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
1.40033 seconds
copy 32768 sectors using a blocksize of 128 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
1.18177 seconds
copy 32768 sectors using a blocksize of 256 sectors  00:01    ( SUCCES )
     	
32768 of 32768 copied
1.19286 seconds
optimal blocksize is 128 sectors (64.00 KiB)
copy 188777901 sectors using a blocksize of 128 sectors  26:52    ( ERROR )
     	
42867757 of 188777901 copied
Error while reading block at sector 43228269
42966061 sectors copied
rollback last transaction  00:00    ( ERROR )
     	
using internal algorithm
copy 42966061 sectors
finding optimal blocksize
     	
copy 32768 sectors using a blocksize of 64 sectors  00:00    ( ERROR )
     	
0.460669 seconds
0 sectors copied
check filesystem on /dev/sde3 for errors and (if possible) fix them  00:00    ( ERROR )
     	
checking is not available for this filesystem
rollback last change to the partitiontable  00:00    ( ERROR )
     	
move partition to the right  00:00    ( ERROR )
     	
old start: 257040
old end: 189133244
old size: 188876205 (90.06 GiB)
libparted messages    ( INFO )
     	
Input/output error during read on /dev/sde
Error opening /dev/sde: No such file or directory
Error opening /dev/sde: No such file or directory

========================================

Create Primary Partition #1 (fat32, 51.87 GiB) on /dev/sde

========================================

---

### Post by kensuguro on 2008-05-02
well, judging from the time it's taking to shut the machine down, I'm just guessing that whatever image gparted may have taken of the the original disk, may be lost.. it's strange because using disk usage analysis, nothing came up as big as the disk size..  but anyway...  this is just a guess.  I'm quite disappointed at this result, not really saying it's anyone's fault.  Bottom line is eveything should be backed up, but still..  I hope there's still a way back.  No more partition editing for me in gparted or parted without a full backup.

---

### Post by kensuguro on 2008-05-04
sorry to bump. but nobody has any advice?

---

### Post by kensuguro on 2008-05-07
should I give up??

---

