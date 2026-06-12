---
title: "External Hard Drive problems"
date: 2008-01-13
forum: General Help
---

### Post by Jesuses Left Leg on 2008-01-13
Hi, I have searched but can't find an answer to this specific problem.
The problem is that I have an external drive connected by usb and it used to mount when it was connected, but now it doesn't. Obviously I could add it to fstab and mount it manually which in itself is no problem but when i do this it mounts fine and then when I try and open it to view files it crashes nautilus and all the files disappear off the desktop (it does eventually restore itself and i can view the drive).

Lsusb sees it
```

matt@matt-laptop:~$ lsusb
Bus 007 Device 006: ID 0bc2:3000 Seagate RSS LLC 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

fdisk -l sees it also as
```

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00020c78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    b  W95 FAT32

```

Ideally I would like to get it back to mounting automatically.
Thanks for any help.
:confused:

---

### Post by Jesuses Left Leg on 2008-01-16
Bump

This is the dmesg after inserting the usb cable.
```

[18491.904000] usb 7-1: new high speed USB device using ehci_hcd and address 3
[18492.052000] usb 7-1: configuration #1 chosen from 1 choice
[18492.068000] APIC error on CPU0: 40(40)
[18492.160000] usbcore: registered new interface driver libusual
[18492.264000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[18492.264000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[18492.272000] Initializing USB Mass Storage driver...
[18492.276000] scsi4 : SCSI emulation for USB Mass Storage devices
[18492.280000] usb-storage: device found at 3
[18492.280000] usb-storage: waiting for device to settle before scanning
[18492.280000] usbcore: registered new interface driver usb-storage
[18492.280000] USB Mass Storage support registered.
[18497.280000] usb-storage: device scan complete
[18497.280000] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
[18497.284000] sd 4:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[18497.284000] sd 4:0:0:0: [sdb] Write Protect is off
[18497.284000] sd 4:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[18497.284000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[18497.288000] sd 4:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[18497.288000] sd 4:0:0:0: [sdb] Write Protect is off
[18497.288000] sd 4:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[18497.288000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[18497.288000]  sdb: sdb1
[18497.320000] sd 4:0:0:0: [sdb] Attached SCSI disk
[18497.320000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[18518.440000] APIC error on CPU0: 40(40)

```

Locking this thread because the problem has solved itself, it just take ages to mount!

Apparently i cant lock it, never mind.

---

