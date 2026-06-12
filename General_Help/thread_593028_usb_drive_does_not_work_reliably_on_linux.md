---
title: "usb drive does not work reliably on linux"
date: 2007-10-26
forum: General Help
---

### Post by kev45 on 2007-10-26
Hi, I'm having problems with my WD Passport 60g usb drive; the device works for a while then for no apparent reason if I try to access files the drive seems to hang. This doesn't happen in windows so there is something wrong with the linux driver or something. I'm using 7.10 gutsy, just upgraded from 7.04 to try to fix the problem to no avail. Here's some output from dmesg - you can see it detects the drive just fine but gets screwy after a while.

```

198.245117] usb 2-1: new high speed USB device using ehci_hcd and address 3
[  198.379426] usb 2-1: configuration #1 chosen from 1 choice
[  198.427769] usbcore: registered new interface driver libusual
[  198.438187] Initializing USB Mass Storage driver...
[  198.438306] scsi4 : SCSI emulation for USB Mass Storage devices
[  198.438398] usb-storage: device found at 3
[  198.438400] usb-storage: waiting for device to settle before scanning
[  198.438492] usbcore: registered new interface driver usb-storage
[  198.438540] USB Mass Storage support registered.
[  203.430301] usb-storage: device scan complete
[  203.433162] scsi 4:0:0:0: Direct-Access     WDC WD60 0UE-32KVT0       0000 PQ: 0 ANSI: 0
[  203.435770] sd 4:0:0:0: [sdb] 117210240 512-byte hardware sectors (60012 MB)
[  203.437142] sd 4:0:0:0: [sdb] Write Protect is off
[  203.437144] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  203.437146] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  203.438763] sd 4:0:0:0: [sdb] 117210240 512-byte hardware sectors (60012 MB)
[  203.440135] sd 4:0:0:0: [sdb] Write Protect is off
[  203.440138] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  203.440139] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  203.440141]  sdb: sdb1
[  203.482344] sd 4:0:0:0: [sdb] Attached SCSI disk
[  203.482371] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 1586.411969] gnect[7409]: segfault at 0000000000000000 rip 00002aaaaaab9ec7 rsp 0000000041801e00 error 4
[31923.774699] usb 2-1: reset high speed USB device using ehci_hcd and address 3
[31933.997175] usb 2-1: reset high speed USB device using ehci_hcd and address 3
[31950.207011] usb 2-1: reset high speed USB device using ehci_hcd and address 3
[31950.454489] usb 2-1: reset high speed USB device using ehci_hcd and address 3
[31960.676952] usb 2-1: reset high speed USB device using ehci_hcd and address 3
[31960.809823] sd 4:0:0:0: scsi: Device offlined - not ready after error recovery
[31960.809832] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[31960.809835] end_request: I/O error, dev sdb, sector 21613821
[31960.809681] sd 4:0:0:0: rejecting I/O to offline device
[31960.809823] sd 4:0:0:0: rejecting I/O to offline device
[31960.812487] sd 4:0:0:0: rejecting I/O to offline device
[31960.812977] sd 4:0:0:0: rejecting I/O to offline device
[31960.819458] sd 4:0:0:0: rejecting I/O to offline device
[31960.819715] sd 4:0:0:0: rejecting I/O to offline device
[31960.819812] FAT: Directory bread(block 160670) failed
[31960.819821] sd 4:0:0:0: rejecting I/O to offline device
[31960.819827] FAT: Directory bread(block 160671) failed
[31960.819832] sd 4:0:0:0: rejecting I/O to offline device
[31960.819838] FAT: Directory bread(block 160672) failed
[31960.819843] sd 4:0:0:0: rejecting I/O to offline device
[31960.819848] FAT: Directory bread(block 160673) failed
[31960.819853] sd 4:0:0:0: rejecting I/O to offline device
[31960.819858] FAT: Directory bread(block 160674) failed
[31960.819863] sd 4:0:0:0: rejecting I/O to offline device
[31960.819868] FAT: Directory bread(block 160675) failed
[31960.819873] sd 4:0:0:0: rejecting I/O to offline device
[31960.819878] FAT: Directory bread(block 160676) failed
[31960.819883] sd 4:0:0:0: rejecting I/O to offline device
[31960.819888] FAT: Directory bread(block 160677) failed

```

I don't like the fact that it's mounted under the scsi emulation crap, but I don't know if there is a real driver out there. Maybe a problem with a usb controller not being supported very well?

Any advice? Thanks!

---

