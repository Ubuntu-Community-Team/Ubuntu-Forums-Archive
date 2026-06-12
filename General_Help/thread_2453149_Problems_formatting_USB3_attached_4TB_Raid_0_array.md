---
title: "Problems formatting USB3 attached 4TB Raid 0 array"
date: 2020-11-04
forum: General Help
---

### Post by David_Partridge on 2020-11-04
LUbuntu 20.04.1

```
root@charon:/home/amonra# lsusb
Bus 002 Device 006: ID 059f:105f LaCie, Ltd 2Big Quadra USB3
```

Trying to format the above drive using mkfs.ext4 /dev/sdc2

Initially got a 120s Kernel timeout which I resolved by setting the timeout to 0

However I got LOTS of message groups in the system log looking like this:

```
Nov 04 06:18:51 charon kernel: scsi host5: uas_eh_device_reset_handler start
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#0 uas_zap_pending 0 uas-tag 1 inflight: 
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#0 CDB: Write Same(10) 41 00 e8 ea 47 fc 00 00 04 00
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#1 uas_zap_pending 0 uas-tag 2 inflight: 
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#1 CDB: Write Same(10) 41 00 e8 e6 48 00 00 ff ff 00
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#2 uas_zap_pending 0 uas-tag 3 inflight: 
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#2 CDB: Write Same(10) 41 00 e8 e9 47 fd 00 ff ff 00
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#3 uas_zap_pending 0 uas-tag 4 inflight: 
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#3 CDB: Write Same(10) 41 00 e8 e8 47 fe 00 ff ff 00
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#4 uas_zap_pending 0 uas-tag 5 inflight: 
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#4 CDB: Write Same(10) 41 00 e8 e7 47 ff 00 ff ff 00
Nov 04 06:18:51 charon kernel: usb 2-1: reset SuperSpeed Gen 1 USB device number 6 using xhci_hcd
Nov 04 06:18:51 charon kernel: scsi host5: uas_eh_device_reset_handler success
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_RESET driverbyte=DRIVER_OK
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#0 CDB: Write Same(10) 41 00 e8 ea 47 fc 00 00 04 00
Nov 04 06:18:51 charon kernel: blk_update_request: I/O error, dev sdc, sector 3907667964 op 0x9:(WRITE_ZEROES) flags 0x1000800 phys_seg 0 prio class 0
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#1 FAILED Result: hostbyte=DID_RESET driverbyte=DRIVER_OK
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#1 CDB: Write Same(10) 41 00 e8 e6 48 00 00 ff ff 00
Nov 04 06:18:51 charon kernel: blk_update_request: I/O error, dev sdc, sector 3907405824 op 0x9:(WRITE_ZEROES) flags 0x1000000 phys_seg 0 prio class 0
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#2 FAILED Result: hostbyte=DID_RESET driverbyte=DRIVER_OK
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#2 CDB: Write Same(10) 41 00 e8 e9 47 fd 00 ff ff 00
Nov 04 06:18:51 charon kernel: blk_update_request: I/O error, dev sdc, sector 3907602429 op 0x9:(WRITE_ZEROES) flags 0x1000000 phys_seg 0 prio class 0
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#3 FAILED Result: hostbyte=DID_RESET driverbyte=DRIVER_OK
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#3 CDB: Write Same(10) 41 00 e8 e8 47 fe 00 ff ff 00
Nov 04 06:18:51 charon kernel: blk_update_request: I/O error, dev sdc, sector 3907536894 op 0x9:(WRITE_ZEROES) flags 0x1000000 phys_seg 0 prio class 0
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#4 FAILED Result: hostbyte=DID_RESET driverbyte=DRIVER_OK
Nov 04 06:18:51 charon kernel: sd 5:0:0:0: [sdc] tag#4 CDB: Write Same(10) 41 00 e8 e7 47 ff 00 ff ff 00
Nov 04 06:18:51 charon kernel: blk_update_request: I/O error, dev sdc, sector 3907471359 op 0x9:(WRITE_ZEROES) flags 0x1000000 phys_seg 0 prio class 0

```

and while the command apparently ended cleanly 

```
root@charon:/home/amonra# mkfs.ext4 /dev/sdc2
mke2fs 1.45.5 (07-Jan-2020)
Creating filesystem with 976701696 4k blocks and 244178944 inodes
Filesystem UUID: f45b0cd6-131a-4a3a-988f-c5a848611445
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000, 550731776, 644972544

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done       

root@charon:/home/amonra# fsck /dev/sdc2
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sdc2: clean, 11/244178944 files, 15615751/976701696 blocks
root@charon:/home/amonra# 

```

I'm not convinced it did ... :(

I searched the web and there were suggestions that I didn't fully understand talking about uas blackisting and reverting to usb?

Questions:

Was I right to worry?

What can be done to fix?

David

---

### Post by TheFu on 2020-11-04
4TB Raid 0 array?
I don't see anything that looks like RAID to Linux in the post above.
Using USB with RAID of any sort is asking for problems.

---

### Post by David_Partridge on 2020-11-05
The raid array is a hardware raid 0 of 2 x 2TB drives.  Just appears to Linux as an external 4TB drive.

My questions still stand.

---

### Post by David_Partridge on 2020-11-05
OK I've managed to determine that this a USB3 UAS problem.   Where do I go to raise this to the attention of the UAS developers?

Thanks
David

---

### Post by David_Partridge on 2020-11-09
I joined the linux-usb mailing list and was advised to blacklist the device for uas:

Created /etc/modprobe.d/blacklist_uas.conf containing text:
 
options usb-storage quirks=059f:105f:u
 
followed by: update-initramfs -u
and rebooted.
 
Now the device works fine and mkfs.ext4 finishes in seconds rather than hours.

A win!
David

---

