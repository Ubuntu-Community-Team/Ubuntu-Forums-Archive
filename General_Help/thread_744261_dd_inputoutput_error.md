---
title: "dd input/output error"
date: 2008-04-03
forum: General Help
---

### Post by rickocop on 2008-04-03
hi I'm trying to create an image of a dvd, but struggling with dd

when I try this: 

```
user@rickslaptop:~$ dd if=/dev/hda of=./fandf.iso 

dd: reading `/dev/dvd': Input/output error
127672+0 records in
127672+0 records out
65368064 bytes (65 MB) copied, 1.76878 seconds, 37.0 MB/s


```

I have also tried with sudo and actually as root.


here is the contents of my dmesg: 
> [ 5465.252000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[ 5465.252000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[ 5465.252000] ide: failed opcode was: unknown
[ 5465.252000] hda: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[ 5465.252000] end_request: I/O error, dev hda, sector 127712
[ 5465.252000] printk: 16 messages suppressed.
[ 5465.252000] Buffer I/O error on device hda, logical block 15964
[ 5465.252000] Buffer I/O error on device hda, logical block 15965
[ 5465.252000] Buffer I/O error on device hda, logical block 15966
[ 5465.252000] Buffer I/O error on device hda, logical block 15967
[ 5465.252000] Buffer I/O error on device hda, logical block 15968
[ 5465.252000] Buffer I/O error on device hda, logical block 15969
[ 5465.252000] Buffer I/O error on device hda, logical block 15970
[ 5465.252000] Buffer I/O error on device hda, logical block 15971
[ 5465.252000] Buffer I/O error on device hda, logical block 15972
[ 5465.252000] Buffer I/O error on device hda, logical block 15973
[ 5465.284000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[ 5465.284000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[ 5465.284000] ide: failed opcode was: unknown
[ 5465.284000] hda: error code: 0x70  sense_key: 0x05  asc: 0x6f  ascq: 0x03
[ 5465.284000] end_request: I/O error, dev hda, sector 127968


---

### Post by mc4man on 2008-04-03
The dvd  has structure protection which in most cases includes unreadable sectors - the dd command has no means to skip these sectors

---

### Post by cdenley on 2008-04-03
> **mc4man said:**
> The dvd  has structure protection which in most cases includes unreadable sectors - the dd command has no means to skip these sectors
The disc is probably scratched or dirty. This command should replace bad blocks with nulls.
```
dd if=/dev/hda of=./fandf.iso conv=noerror,sync
```
Of course, the image wouldn't be completely functional.

---

### Post by mc4man on 2008-04-04
> The disc is probably scratched or dirty. This command should replace bad blocks with nulls.
if what the O.P. was was dumping was a commercial dvd then the errors are more likely due to structure protection than physical damage or stamping defects. In any event using dd on a less than pristine disk is ill advised and in the case of S.P. disks a waste of time even with above posted command. For example on a known S.P. disk - 
Straight up dd
```
 dd if=/dev/scd1 of=cd.iso
dd: reading `/dev/scd1': Input/output error
1053920+0 records in
1053920+0 records out
539607040 bytes (540 MB) copied, 80.6629 seconds, 6.7 MB/s
```
with added command - clipped and aborted after 10 min.
```
dd if=/dev/scd1 of=cd.iso conv=noerror,sync
dd: reading `/dev/scd1': Input/output error
898784+0 records in
898784+0 records out
460177408 bytes (460 MB) copied, 59.7194 seconds, 7.7 MB/s
dd: reading `/dev/scd1': Input/output error
898784+1 records in
898785+0 records out
460177920 bytes (460 MB) copied, 59.7196 seconds, 7.7 MB/s
...........................................
469167616 bytes (469 MB) copied, 686.307 seconds, 684 kB/s
dd: reading `/dev/scd1': Input/output error
905816+10528 records in
916344+0 records out
469168128 bytes (469 MB) copied, 686.4 seconds, 684 kB/s
905816+10529 records in
916344+0 records out
469168128 bytes (469 MB) copied, 686.401 seconds, 684 kB/s


```
better way - took 20 sec. to fast skip @ 16 sectors per block, 1 read retry per block (plus decyrpted)
```
Writing to /home/doug/xxxxxx/VIDEO_TS/VIDEO_TS.BUP 
  28kB of   28kB written
[Info] 
Writing to /home/doug/xxxxxxx/VIDEO_TS/VIDEO_TS.IFO 
  28kB of   28kB written
[Info] 
Writing to /home/doug/xxxxxx/VIDEO_TS/VIDEO_TS.VOB 
 438MB of  438MB written ( 100.0% )  
[Info] 
Writing to /home/doug/xxxxxx/VIDEO_TS/VTS_01_0.BUP 
  86kB of   86kB written
[Info] 
Writing to /home/doug/xxxxxx/VIDEO_TS/VTS_01_0.IFO 
  86kB of   86kB written
[Info] 
Writing to /home/doug/xxxxxx/VIDEO_TS/VTS_01_0.VOB 
  74MB of   75MB written ( 100.0% ) 
[Info] 
Writing to /home/doug/xxxxxxxxxxxx/VTS_01_1.VOB 
[Warn] Had to skip 0 blocks!  [Warn] Had to skip 1 blocks!  [Warn] Had to skip 2 blocks!  [Warn] Had to skip 3 blocks!  [Warn] Had to skip 4 blocks!     1MB of [Warn] Had to skip 5 blocks!  [Warn] Had to skip 6 blocks!  [Warn] Had to skip 7 blocks! 1024MB of 1024MB written ( 100.0% )
```
If your not prepared or able to fix issues created by bad sectors, ie. adjust vob pointers, remove unreferenced cells ect.,  then in the case of S.P. disks using something like k9copy would be best bet
In addition all dvd drives will slow down when encountering read errors, some can regain close to full speed when the # of or time spent getting past is limited

---

