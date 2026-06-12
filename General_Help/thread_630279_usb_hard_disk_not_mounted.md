---
title: "usb hard disk not mounted"
date: 2007-12-03
forum: General Help
---

### Post by g.a. on 2007-12-03
Hi,

I'm using a digital player with hard-disk. I can use it from winxp and drag&drop files.

I'm not able to do it from kubuntu. With kubuntu 7.04 I had a kernel oops, now I upgrated to kubuntu 7.10, I do not receive anymore a kernel oops but the hard-disk is not mounted as well. 

Below is the dmesg output, just as information I formatted the external hard-disk as FAT32 under WindowsXP.

The dmesg output is:

[ 9592.760000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[ 9593.060000] usb 4-3: configuration #1 chosen from 1 choice
[ 9593.060000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 9593.060000] usb-storage: device found at 4
[ 9593.060000] usb-storage: waiting for device to settle before scanning
[ 9598.060000] usb-storage: device scan complete
[ 9598.060000] scsi 3:0:0:0: Direct-Access     OSI      HDD Jukebox      0100 PQ: 0 ANSI: 4
[ 9598.060000] sd 3:0:0:0: [sdb] 15615133 512-byte hardware sectors (7995 MB)
[ 9598.064000] sd 3:0:0:0: [sdb] Write Protect is off
[ 9598.064000] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 9598.064000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 9598.064000] sd 3:0:0:0: [sdb] 15615133 512-byte hardware sectors (7995 MB)
[ 9598.064000] sd 3:0:0:0: [sdb] Write Protect is off
[ 9598.064000] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 9598.064000] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 9598.064000]  sdb:<6>usb 4-3: USB disconnect, address 4
[ 9600.148000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9600.148000] end_request: I/O error, dev sdb, sector 0
[ 9600.148000] Buffer I/O error on device sdb, logical block 0
[ 9600.148000] Buffer I/O error on device sdb, logical block 1
[ 9600.148000] Buffer I/O error on device sdb, logical block 2
[ 9600.148000] Buffer I/O error on device sdb, logical block 3
[ 9600.148000] Buffer I/O error on device sdb, logical block 4
[ 9600.148000] Buffer I/O error on device sdb, logical block 5
[ 9600.148000] Buffer I/O error on device sdb, logical block 6
[ 9600.148000] Buffer I/O error on device sdb, logical block 7
[ 9600.148000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9600.148000] end_request: I/O error, dev sdb, sector 0
[ 9600.148000] Buffer I/O error on device sdb, logical block 0
[ 9600.148000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9600.148000] end_request: I/O error, dev sdb, sector 1
[ 9600.148000] Buffer I/O error on device sdb, logical block 1
[ 9600.152000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9600.152000] end_request: I/O error, dev sdb, sector 0
[ 9600.152000] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 9600.152000] end_request: I/O error, dev sdb, sector 1


thanks,
g.

---

### Post by skyjacker on 2007-12-03
Here is how I got my external HD to accept drag & drop: 1)  Open system Menu and left click storage media.
2) Place the cursor over the item you need mount4ed and right click
3) Choose "Properties in the drop down menu
4) In the "Tab" area choose "Mounting"
5) If "Mount as user" is checked, uncheck it. Worked for me hope it will for you also. P.S. I can't explain why it worked, it just did.

---

### Post by g.a. on 2007-12-04
thanks for the reply,

my problem is somehow different and my post was maybe not so clear, the external hard-disk is not mounted at all, here is the corresponding content of /var/log/messages

Dec  4 09:17:47 neo kernel: [  726.184000] usb 4-3: new high speed USB device using ehci_hcd and address 3
Dec  4 09:17:47 neo kernel: [  726.492000] usb 4-3: configuration #1 chosen from 1 choice
Dec  4 09:17:48 neo kernel: [  727.132000] usbcore: registered new interface driver libusual
Dec  4 09:17:48 neo kernel: [  727.288000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec  4 09:17:48 neo kernel: [  727.288000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec  4 09:17:48 neo kernel: [  727.472000] Initializing USB Mass Storage driver...
Dec  4 09:17:48 neo kernel: [  727.476000] scsi2 : SCSI emulation for USB Mass Storage devices
Dec  4 09:17:48 neo kernel: [  727.476000] usbcore: registered new interface driver usb-storage
Dec  4 09:17:48 neo kernel: [  727.476000] USB Mass Storage support registered.
Dec  4 09:17:52 neo kernel: [  731.712000] usb 4-3: USB disconnect, address 3
Dec  4 09:17:57 neo kernel: [  736.540000] usb 4-3: new high speed USB device using ehci_hcd and address 4
Dec  4 09:17:58 neo kernel: [  737.344000] usb 4-3: new high speed USB device using ehci_hcd and address 5
Dec  4 09:17:58 neo kernel: [  737.888000] usb 4-3: new high speed USB device using ehci_hcd and address 6
Dec  4 09:17:59 neo kernel: [  738.408000] usb 4-3: new high speed USB device using ehci_hcd and address 7


best,
g.

---

