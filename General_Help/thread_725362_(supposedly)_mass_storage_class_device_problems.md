---
title: "(supposedly) mass storage class device problems"
date: 2008-03-15
forum: General Help
---

### Post by minordemocritus on 2008-03-15
i'm having issues with a supposedly usb mass storage class device not persisting in /dev... the dmesg logs show detection and assignment to /dev/sdb 1 and 2, but when i try to mount it, cat it, or fdisk it, /dev/sdb doesn't exist... it assumes write through for drive caching, i have a feeling that has something to do with it... the device is a Zoom HD16CD multitrack recorder, and i'm using ubuntu studio, but the problems happened with an older version of ubuntu as well as the latest knoppix...

the relevant dmesg lines:
[ 1701.453621] usb 1-6: new high speed USB device using ehci_hcd and address 2
[ 1701.576474] usb 1-6: configuration #1 chosen from 1 choice
[ 1701.643812] usbcore: registered new interface driver libusual
[ 1701.683842] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 1701.683853] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 1701.693156] Initializing USB Mass Storage driver...
[ 1701.694002] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1701.694280] usbcore: registered new interface driver usb-storage
[ 1701.694286] USB Mass Storage support registered.
[ 1701.694456] usb-storage: device found at 2
[ 1701.694460] usb-storage: waiting for device to settle before scanning
[ 1706.681427] usb-storage: device scan complete
[ 1706.683928] scsi 4:0:0:0: Direct-Access ZOOM HD 0.00 PQ: 0 ANSI: 2
[ 1706.694618] sd 4:0:0:0: [sdb] 156301489 512-byte hardware sectors (80026 MB)
[ 1706.698108] sd 4:0:0:0: [sdb] Write Protect is off
[ 1706.698115] sd 4:0:0:0: [sdb] Mode Sense: 87 00 00 08
[ 1706.698119] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1706.702841] sd 4:0:0:0: [sdb] 156301489 512-byte hardware sectors (80026 MB)
[ 1706.706205] sd 4:0:0:0: [sdb] Write Protect is off
[ 1706.706212] sd 4:0:0:0: [sdb] Mode Sense: 87 00 00 08
[ 1706.706215] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1706.706221] sdb: sdb1 sdb2
[ 1706.729932] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 1706.730005] sd 4:0:0:0: Attached scsi generic sg2 type 0

**AFTER DEVICE REMOVAL:

[ 1736.887275] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[ 1767.021231] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[ 1797.155193] usb 1-6: reset high speed USB device using ehci_hcd and address 2
[ 1824.889312] usb 1-6: USB disconnect, address 2
[ 1824.889345] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1824.889353] end_request: I/O error, dev sdb, sector 156301488
[ 1824.889359] Buffer I/O error on device sdb, logical block 156301488
[ 1824.889453] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1824.889459] end_request: I/O error, dev sdb, sector 156301488
[ 1824.889463] Buffer I/O error on device sdb, logical block 156301488
[ 1824.889516] Buffer I/O error on device sdb, logical block 156301480
**Previous line repeats 7 more times, going up sequentially in block number
[ 1824.889845] scsi 4:0:0:0: rejecting I/O to dead device
**Previous line repeats about 50 times

i'll post the relevant output of lsusb -v and fdisk -l when i get back to the machine....

any ideas?

---

