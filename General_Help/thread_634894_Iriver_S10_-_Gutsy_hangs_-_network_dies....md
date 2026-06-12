---
title: "Iriver S10 - Gutsy hangs - network dies..."
date: 2007-12-08
forum: General Help
---

### Post by bender05 on 2007-12-08
When I plug in my Iriver s10 UMS mp3 player it automounts and Nautilus opens a window and displays the contents - however soon after Gutsy hangs and I believe this is because my usb wifi adaptor has died - please see kernel log extract below...

Any advice gratefully received

[COLOR="Blue"]Dec  7 20:00:41 Jupiter kernel: [10221.235455] usb 5-7: new high speed USB device using ehci_hcd and address 5
Dec  7 20:00:41 Jupiter kernel: [10221.368835] usb 5-7: configuration #1 chosen from 1 choice
Dec  7 20:00:41 Jupiter kernel: [10221.430820] usbcore: registered new interface driver libusual
Dec  7 20:00:41 Jupiter kernel: [10221.464145] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec  7 20:00:41 Jupiter kernel: [10221.464322] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec  7 20:00:41 Jupiter kernel: [10221.471296] Initializing USB Mass Storage driver...
Dec  7 20:00:41 Jupiter kernel: [10221.471549] scsi4 : SCSI emulation for USB Mass Storage devices
Dec  7 20:00:41 Jupiter kernel: [10221.471769] usb-storage: device found at 5
Dec  7 20:00:41 Jupiter kernel: [10221.471773] usb-storage: waiting for device to settle before scanning
Dec  7 20:00:41 Jupiter kernel: [10221.472055] usbcore: registered new interface driver usb-storage
Dec  7 20:00:41 Jupiter kernel: [10221.472211] USB Mass Storage support registered.
Dec  7 20:00:46 Jupiter kernel: [10226.468882] usb-storage: device scan complete
Dec  7 20:00:46 Jupiter kernel: [10226.469449] scsi 4:0:0:0: Direct-Access     iriver   S10              0.83 PQ: 0 ANSI: 2
Dec  7 20:00:46 Jupiter kernel: [10226.471183] sd 4:0:0:0: [sdb] 3991552 512-byte hardware sectors (2044 MB)
Dec  7 20:00:46 Jupiter kernel: [10226.471810] sd 4:0:0:0: [sdb] Write Protect is off
Dec  7 20:00:46 Jupiter kernel: [10226.471816] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
Dec  7 20:00:46 Jupiter kernel: [10226.471822] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Dec  7 20:00:46 Jupiter kernel: [10226.473541] sd 4:0:0:0: [sdb] 3991552 512-byte hardware sectors (2044 MB)
Dec  7 20:00:46 Jupiter kernel: [10226.474165] sd 4:0:0:0: [sdb] Write Protect is off
Dec  7 20:00:46 Jupiter kernel: [10226.474171] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
Dec  7 20:00:46 Jupiter kernel: [10226.474176] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Dec  7 20:00:46 Jupiter kernel: [10226.474181]  sdb: unknown partition table
Dec  7 20:00:46 Jupiter kernel: [10226.494329] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Dec  7 20:00:46 Jupiter kernel: [10226.494400] sd 4:0:0:0: Attached scsi generic sg3 type 0
Dec  7 20:00:50 Jupiter kernel: [10230.366513] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:51 Jupiter kernel: [10231.389950] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:52 Jupiter kernel: [10232.413391] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:53 Jupiter kernel: [10233.436839] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:54 Jupiter kernel: [10234.456282] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:55 Jupiter kernel: [10235.479730] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:56 Jupiter kernel: [10236.499181] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:57 Jupiter kernel: [10237.526657] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:58 Jupiter kernel: [10238.550067] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:00:59 Jupiter kernel: [10239.577517] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:01:00 Jupiter kernel: [10240.596964] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:01:01 Jupiter kernel: [10241.620407] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:01:02 Jupiter kernel: [10242.639853] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:01:03 Jupiter kernel: [10243.667294] zd1211rw 5-4:1.0: error ioread32(CR_REG1): -110
Dec  7 20:01:30 Jupiter kernel: [10270.634448] usb 5-7: USB disconnect, address 5
Dec  7 20:01:30 Jupiter kernel: [10270.634846] Buffer I/O error on device sdb, logical block 496
Dec  7 20:01:30 Jupiter kernel: [10270.634854] lost page write due to I/O error on sdb
Dec  7 20:01:30 Jupiter kernel: [10270.681644] scsi 4:0:0:0: rejecting I/O to dead device[/COLOR]


Many thanks

Nigel

---

### Post by geraldm on 2007-12-09
I can not help completely, but I would start checking the device sdb.
The clue is "unknown partition table", but later a write instruction fails, which would be expected when the partition table is unknown.  The software should not be writing when the partition
table is unknown.  I suspect it is related to the iRiver device which is device sdb.
I would suspect the usb-storage driver.
A test of write to the wifi can be done without use of the iRiver to provide some clues about the use of the wifi. 

Gerald

---

### Post by bender05 on 2007-12-09
I think you are right - the wifi works perfectly and consistently until the Iriver is plugged in.

I have reformatted the Iriver and "Windows XP" reports it as FAT16 - but if I try to look at it using Gnome Partition Editor it comes up as unknown partition table - might try and see what happens if I plug it in without the wifi plugged in....

---

### Post by bender05 on 2007-12-09
No same symptoms without wifi card plugged in.... anyone else experienced symptoms like this??

---

### Post by jcsjcs on 2008-01-18
> **bender05 said:**
> No same symptoms without wifi card plugged in.... anyone else experienced symptoms like this??

I've just fought with my Buffalo WLI-U2-KG54L for the last 6 hours or so. It worked nicely a day ago (just bought it then), and wouldn't work again the next morning. I thought the only difference between yesterday and today was that I upgraded my Debian distribution, but this thread brought to my attention that I have plugged in my USB hub.

I'm getting a variety of ioread32 errors and my wireless adapter will not find any networks. If I unplug my USB hub (and un- and replug my wireless adapter), everything works fine, even if I plug in the USB hub afterwards.

Quite strange...

This is what is reported when I plug in my USB hub:

Jan 19 02:22:18 hatarakibachi kernel: [ 3744.644772] usb 1-3: new high speed USB device using ehci_hcd and address 28
Jan 19 02:22:18 hatarakibachi kernel: [ 3744.692826] usb 1-3: configuration #1 chosen from 1 choice
Jan 19 02:22:18 hatarakibachi kernel: [ 3744.693093] hub 1-3:1.0: USB hub found
Jan 19 02:22:18 hatarakibachi kernel: [ 3744.699868] hub 1-3:1.0: 4 ports detected
Jan 19 02:22:18 hatarakibachi NetworkManager: <debug> [1200676938.978025] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5e3_605_noserial'). 
Jan 19 02:22:19 hatarakibachi NetworkManager: <debug> [1200676939.009135] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 

I hope this report helps other people trying to figure out why their wireless doesn't work.

JCS.

---

