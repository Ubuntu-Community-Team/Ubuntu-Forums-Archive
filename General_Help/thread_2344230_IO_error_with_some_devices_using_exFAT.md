---
title: "I/O error with some devices using exFAT"
date: 2016-11-23
forum: General Help
---

### Post by jirkarck01 on 2016-11-23
Hi, I have a problem with my exFAT formatted MP4 device. I have already installed exFAT fuse v1.2.3. I am able to mount exfat devices and browse files now. But if I try to read or write anything, it ends immediately with I/O error. Once, one file was copied to my computer, but it was corrupted. Maybe, it is problem of my MP4 device (because I have tried it also with flashdisk and it works ok). But if I connect MP4 device on Windows, file system it is not corrupted. I can mount it, scandisk isn't recommended and I can read everything on device.


How poor is the implementation of exFAT in Linux? Is there any better package which can work with exFAT?

dmesg output:
```

[ 3170.728075] usb-storage 2-3.3.3:1.0: USB Mass Storage device detected
[ 3170.729067] scsi host15: usb-storage 2-3.3.3:1.0
[ 3171.165150] usb 2-3.3.3: USB disconnect, device number 34
[ 3171.365534] usb 2-3.3.3: new high-speed USB device number 35 using xhci_hcd
[ 3171.455591] usb 2-3.3.3: New USB device found, idVendor=4255, idProduct=1000
[ 3171.455595] usb 2-3.3.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3171.455596] usb 2-3.3.3: Product: Storage
[ 3171.455598] usb 2-3.3.3: Manufacturer: Ambarella
[ 3171.455599] usb 2-3.3.3: SerialNumber: 123456789ABC
[ 3171.456194] usb-storage 2-3.3.3:1.0: USB Mass Storage device detected
[ 3171.456346] scsi host16: usb-storage 2-3.3.3:1.0
[ 3176.557881] usb 2-3.3.3: reset high-speed USB device number 35 using xhci_hcd
[ 3176.662721] scsi 16:0:0:0: Direct-Access     AMBA     Storage          v1.0 PQ: 0 ANSI: 4
[ 3176.663173] sd 16:0:0:0: Attached scsi generic sg1 type 0
[ 3176.664169] sd 16:0:0:0: [sdb] 121061376 512-byte logical blocks: (62.0 GB/57.7 GiB)
[ 3176.664772] sd 16:0:0:0: [sdb] Write Protect is off
[ 3176.664778] sd 16:0:0:0: [sdb] Mode Sense: ad 00 00 08
[ 3176.667349] sd 16:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 3176.905783]  sdb: sdb1
[ 3176.910654] sd 16:0:0:0: [sdb] Attached SCSI removable disk
[ 3302.540009] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3302.540015] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 01 01 e0 00 00 20 00
[ 3302.540018] blk_update_request: I/O error, dev sdb, sector 66016
[ 3315.568471] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3315.568475] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 01 01 e0 00 00 20 00
[ 3315.568477] blk_update_request: I/O error, dev sdb, sector 66016
[ 3315.724354] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3315.724359] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 20 00 00 18 00
[ 3315.724361] blk_update_request: I/O error, dev sdb, sector 32
[ 3315.764810] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3315.764814] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 00 40 00 00 38 00
[ 3315.764816] blk_update_request: I/O error, dev sdb, sector 64
[ 3315.948158] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3315.948162] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 02 f0 00 00 10 00
[ 3315.948165] blk_update_request: I/O error, dev sdb, sector 752
[ 3316.340254] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3316.340258] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 03 f0 00 00 10 00
[ 3316.340260] blk_update_request: I/O error, dev sdb, sector 1008
[ 3316.412346] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3316.412350] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 01 03 f0 00 00 10 00
[ 3316.412352] blk_update_request: I/O error, dev sdb, sector 66544
[ 3316.488268] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3316.488273] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 03 28 00 00 08 00
[ 3316.488275] blk_update_request: I/O error, dev sdb, sector 808
[ 3316.488278] Buffer I/O error on dev sdb, logical block 101, async page read
[ 3342.397398] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3342.397403] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 80 08 00 00 08 00
[ 3342.397406] blk_update_request: I/O error, dev sdb, sector 32776
[ 3342.437376] sd 16:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
[ 3342.437380] sd 16:0:0:0: [sdb] tag#0 CDB: Read(10) 28 00 00 00 80 08 00 00 08 00
[ 3342.437383] blk_update_request: I/O error, dev sdb, sector 32776
[ 3342.437389] Buffer I/O error on dev sdb1, logical block 1, async page read

```

---

### Post by DuckHook on 2016-11-23
ExFAT is a proprietary MS technology that MS holds patents on, so its Linux implementation is problematic, both legally and technically. The fuse implementation is a result of reverse engineering, which is always touch and go, and is incomplete. I last used ExFAT fuse some years ago so my technical understanding is rusty, but I had no problems with it. I stopped using it because I didn't like its restricted nature, its non-kernel operations, and is questionable legal status, so I reformatted all of my large SD cards to ext2 and got rid of it. I appreciate that not everyone can use this option.

I am on the road right now so am of limited help to you. Hopefully, other forum members will see this thread and offer some suggestions.

---

### Post by jirkarck01 on 2016-11-25
Thank you for reply. Unfortunetely, FW of MP4 device can't work with EXT, FAT32 nor NTFS, so I can't use it with Ubuntu.

---

