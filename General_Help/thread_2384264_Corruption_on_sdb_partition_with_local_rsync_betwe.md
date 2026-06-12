---
title: "Corruption on sdb partition with local rsync between physical drives."
date: 2018-02-04
forum: General Help
---

### Post by Lin_Mast on 2018-02-04
Ubuntu 16.04.3 LTS
kernel: 4.4.0-112-generic #135-Ubuntu SMP Fri Jan 19 11:48:36 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
NVIDIA ION Atom 330 system (Intel(R) Atom(TM) CPU  330   @ 1.60GHz)

When running rsync'ing a large directory of media files from a directory on HDD sda1 to a local, mounted directory on HDD sdb1 (separate physical hard drives, but same motherboard controller), the sdb1 HDD partition drops off and the HDD sdb becomes unreachable (smartctl -a /dev/sdb says 600 PB drive - obviously an error) until a reboot. Whatever happends also corrupts the ext4 filesystem.

```
Feb  4 11:16:53 localhost kernel: [  683.044257] sd 1:0:0:0: [sdb] tag#8 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.044273] sd 1:0:0:0: [sdb] tag#8 CDB: Synchronize Cache(10) 35 00 00 00 00 00 00 00 00 00
Feb  4 11:16:53 localhost kernel: [  683.044299] blk_update_request: I/O error, dev sdb, sector 2048
Feb  4 11:16:53 localhost kernel: [  683.044312] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.044386] EXT4-fs (sdb1): Delayed block allocation failed for inode 117178470 at logical offset 6144 with max blocks 2048 with error 5
Feb  4 11:16:53 localhost kernel: [  683.044400] EXT4-fs (sdb1): This should not happen!! Data will be lost
Feb  4 11:16:53 localhost kernel: [  683.053828] sd 1:0:0:0: [sdb] tag#9 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.053845] sd 1:0:0:0: [sdb] tag#9 CDB: Read(10) 28 00 1a 40 08 68 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.053852] blk_update_request: I/O error, dev sdb, sector 440404072
Feb  4 11:16:53 localhost kernel: [  683.053900] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1693, block_bitmap = 55050253
Feb  4 11:16:53 localhost kernel: [  683.053914] EXT4-fs (sdb1): previous I/O error to superblock detected
Feb  4 11:16:53 localhost kernel: [  683.054003] sd 1:0:0:0: [sdb] tag#10 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.054016] sd 1:0:0:0: [sdb] tag#10 CDB: Write(10) 2a 00 00 00 08 00 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.054023] blk_update_request: I/O error, dev sdb, sector 2048
Feb  4 11:16:53 localhost kernel: [  683.054033] blk_update_request: I/O error, dev sdb, sector 2048
Feb  4 11:16:53 localhost kernel: [  683.054042] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.054164] sd 1:0:0:0: [sdb] tag#11 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.054177] sd 1:0:0:0: [sdb] tag#11 CDB: Read(10) 28 00 1a 40 08 70 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.054184] blk_update_request: I/O error, dev sdb, sector 440404080
Feb  4 11:16:53 localhost kernel: [  683.054219] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1694, block_bitmap = 55050254
Feb  4 11:16:53 localhost kernel: [  683.054228] EXT4-fs (sdb1): previous I/O error to superblock detected
Feb  4 11:16:53 localhost kernel: [  683.054284] sd 1:0:0:0: [sdb] tag#12 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.054296] sd 1:0:0:0: [sdb] tag#12 CDB: Write(10) 2a 00 00 00 08 00 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.054303] blk_update_request: I/O error, dev sdb, sector 2048
Feb  4 11:16:53 localhost kernel: [  683.054312] blk_update_request: I/O error, dev sdb, sector 2048
Feb  4 11:16:53 localhost kernel: [  683.054320] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.054420] sd 1:0:0:0: [sdb] tag#13 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.054432] sd 1:0:0:0: [sdb] tag#13 CDB: Read(10) 28 00 1a 40 08 78 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.054439] blk_update_request: I/O error, dev sdb, sector 440404088
Feb  4 11:16:53 localhost kernel: [  683.054472] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1695, block_bitmap = 55050255
Feb  4 11:16:53 localhost kernel: [  683.054481] EXT4-fs (sdb1): previous I/O error to superblock detected
Feb  4 11:16:53 localhost kernel: [  683.054536] sd 1:0:0:0: [sdb] tag#14 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.054549] sd 1:0:0:0: [sdb] tag#14 CDB: Write(10) 2a 00 00 00 08 00 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.054556] blk_update_request: I/O error, dev sdb, sector 2048
Feb  4 11:16:53 localhost kernel: [  683.054565] blk_update_request: I/O error, dev sdb, sector 2048
Feb  4 11:16:53 localhost kernel: [  683.054574] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.054682] sd 1:0:0:0: [sdb] tag#15 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.054694] sd 1:0:0:0: [sdb] tag#15 CDB: Read(10) 28 00 1a 80 08 00 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.054727] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1696, block_bitmap = 55574528
Feb  4 11:16:53 localhost kernel: [  683.054736] EXT4-fs (sdb1): previous I/O error to superblock detected
Feb  4 11:16:53 localhost kernel: [  683.054791] sd 1:0:0:0: [sdb] tag#16 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.054803] sd 1:0:0:0: [sdb] tag#16 CDB: Write(10) 2a 00 00 00 08 00 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.054815] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.054914] sd 1:0:0:0: [sdb] tag#17 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Feb  4 11:16:53 localhost kernel: [  683.054926] sd 1:0:0:0: [sdb] tag#17 CDB: Read(10) 28 00 1a 80 08 08 00 00 08 00
Feb  4 11:16:53 localhost kernel: [  683.054958] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1697, block_bitmap = 55574529
Feb  4 11:16:53 localhost kernel: [  683.054967] EXT4-fs (sdb1): previous I/O error to superblock detected
Feb  4 11:16:53 localhost kernel: [  683.055020] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.055131] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1698, block_bitmap = 55574530
Feb  4 11:16:53 localhost kernel: [  683.055140] EXT4-fs (sdb1): previous I/O error to superblock detected
Feb  4 11:16:53 localhost kernel: [  683.055192] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.055305] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1699, block_bitmap = 55574531
Feb  4 11:16:53 localhost kernel: [  683.055314] EXT4-fs (sdb1): previous I/O error to superblock detected
Feb  4 11:16:53 localhost kernel: [  683.055366] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.055476] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1700, block_bitmap = 55574532
Feb  4 11:16:53 localhost kernel: [  683.055486] EXT4-fs (sdb1): previous I/O error to superblock detected
Feb  4 11:16:53 localhost kernel: [  683.055538] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.055657] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1701, block_bitmap = 55574533
Feb  4 11:16:53 localhost kernel: [  683.055714] Buffer I/O error on dev sdb1, logical block 0, lost sync page write
Feb  4 11:16:53 localhost kernel: [  683.055823] EXT4-fs error (device sdb1): ext4_wait_block_bitmap:503: comm rsync: Cannot read block bitmap - block_group = 1702, block_bitmap = 55574534
Feb  4 11:16:53 localhost kernel: [  683.229502] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 33558528 size 8388608 starting block 262504960)
Feb  4 11:16:53 localhost kernel: [  683.229519] Buffer I/O error on device sdb1, logical block 262504448
Feb  4 11:16:53 localhost kernel: [  683.229535] Buffer I/O error on device sdb1, logical block 262504449
Feb  4 11:16:53 localhost kernel: [  683.229544] Buffer I/O error on device sdb1, logical block 262504450
Feb  4 11:16:53 localhost kernel: [  683.229554] Buffer I/O error on device sdb1, logical block 262504451
Feb  4 11:16:53 localhost kernel: [  683.229563] Buffer I/O error on device sdb1, logical block 262504452
Feb  4 11:16:53 localhost kernel: [  683.229573] Buffer I/O error on device sdb1, logical block 262504453
Feb  4 11:16:53 localhost kernel: [  683.229583] Buffer I/O error on device sdb1, logical block 262504454
Feb  4 11:16:53 localhost kernel: [  683.229592] Buffer I/O error on device sdb1, logical block 262504455
Feb  4 11:16:53 localhost kernel: [  683.229601] Buffer I/O error on device sdb1, logical block 262504456
Feb  4 11:16:53 localhost kernel: [  683.229610] Buffer I/O error on device sdb1, logical block 262504457
Feb  4 11:16:53 localhost kernel: [  683.229997] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 33558528 size 8388608 starting block 262505216)
Feb  4 11:16:53 localhost kernel: [  683.230374] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 33558528 size 8388608 starting block 262505472)
Feb  4 11:16:53 localhost kernel: [  683.230746] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 33558528 size 8388608 starting block 262505728)
Feb  4 11:16:53 localhost kernel: [  683.231117] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 33558528 size 8388608 starting block 262505984)
Feb  4 11:16:53 localhost kernel: [  683.231486] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 33558528 size 8388608 starting block 262506240)
Feb  4 11:16:53 localhost kernel: [  683.231851] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 33558528 size 8388608 starting block 262506496)
Feb  4 11:16:53 localhost kernel: [  683.232324] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 33558528 size 8388608 starting block 262506752)
Feb  4 11:16:53 localhost kernel: [  683.251070] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 41947136 size 8384512 starting block 262507008)
Feb  4 11:16:53 localhost kernel: [  683.251760] EXT4-fs warning (device sdb1): ext4_end_bio:330: I/O error -5 writing to inode 117178470 (offset 41947136 size 8384512 starting block 262507264)
Feb  4 11:16:53 localhost kernel: [  683.441292] JBD2: Detected IO errors while flushing file data on sdb1-8
Feb  4 11:16:53 localhost kernel: [  683.441330] Aborting journal on device sdb1-8.
Feb  4 11:16:53 localhost kernel: [  683.441471] JBD2: Error -5 detected when updating journal superblock for sdb1-8.
Feb  4 11:16:53 localhost kernel: [  683.442379] JBD2: Detected IO errors while flushing file data on sdb1-8
Feb  4 11:16:53 localhost kernel: [  683.567330] EXT4-fs error (device sdb1): ext4_journal_check_start:56: Detected aborted journal
```

Things I have tried (in order):

[LIST=1]
[*]I always check sdb1 with e2fsck -f while offline and be sure it is 'clean' before mounting 
[*]checked HDD sdb with WD utils - OK and SMART data for the drive is OK, including extended self-test under bootable DOS. 
[*]installed new HDD sdb (WD Red 2 TB) 
[*]installed a new SATA cable with locking connectors for HDD sdb 
[*]tried moving SATA cable for sdb to other SATA controller ports on motherboard 
[*]changed BIOS type from SATA to AHCI setting 
[/LIST]
None of these has corrected the failures.

At first I was thinking HDD failure (replaced it), then I was thinking controller failure (but works fine under bootable DOS and chkdsk), but now I am wondering about a kernel problem that surfaces under heavy load caused by rsync.

BTW, the boot HDD sda is a similar (but older) WD 2T drive and is rock stable with no errors, both on the same on motherboard SATA controller.

If I run from bootable DOS utilities, I get no errors from either drive, which makes me think kernel problem.

Any ideas to troubleshoot (or fix this error) further.

---

### Post by wildmanne39 on 2018-02-04
*Thread moved to **General Help, a more appropriate forum**.*

---

### Post by TheFu on 2018-02-04
Sounds like you've done all the normal trouble shooting and seems you are left with a BIOS issue or HW issue on the motherboard.

I move large files around with rsync all-the-time.  Never see this issue.

However, certain Atom systems are known to have problems with high loads.  I didn't think the issues were seen with local workloads. High network loads were the issues, I believe.  [https://www.theregister.co.uk/2017/02/06/cisco_intel_decline_to_link_product_warning_to_faulty_chip/](https://www.theregister.co.uk/2017/02/06/cisco_intel_decline_to_link_product_warning_to_faulty_chip/)
and
[https://community.ubnt.com/t5/UniFi-Routing-Switching/Intel-Atom-C2000-Failures/td-p/1827561](https://community.ubnt.com/t5/UniFi-Routing-Switching/Intel-Atom-C2000-Failures/td-p/1827561)

Don't know if an Atom 330 is part of the C2000 family.

---

### Post by Lin_Mast on 2018-02-04
I just confirmed that the Atom 330 is not a member of the Atom C2000 family.
A few more items (if they provide any clues):
The error only seems to occur on drive being written to by rsync (no errors on the source drive of the same type and on same motherboard controller).
Externally bootable disk imaging software such as Acronis seemed to work OK.

---

### Post by TheFu on 2018-02-05
Excellent research.

I'd swap the SATA ports around on the MB side. Never know, though you have done good to rule that out.

Have you tried a few different kernels yet?  4.5, 4.6, 4.7, 4.8, .... are all possible.

---

### Post by Lin_Mast on 2018-02-27
SOLVED
I have found the cause - A 'flaky' (intermittent/noisy) power connector to the SATA drive.  The power checked OK with a multimeter, but same problem happened on 2 different drives with that power connector.  Not enough disruption to stop the drive, but enough to cause drive interface errors.  Wish there was SMART data on these drives about power problems.  Thanks for all of the help.

---

### Post by DuckHook on 2018-02-27
=d>

I will just say that you not only solved this one on your own, but cracked a very hard nut in doing so. HW problems of the type you chased down are very difficult to diagnose. The fact that you solved it is quite admirable. Your willingness to report back for the benefit of others is also very much appreciated.

Good Luck and Happy Ubuntu-ing!

---

