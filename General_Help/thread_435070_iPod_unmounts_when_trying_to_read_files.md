---
title: "iPod unmounts when trying to read files"
date: 2007-05-06
forum: General Help
---

### Post by pjman on 2007-05-06
I just upgraded my sister from XP to Ubuntu 7.04. Before the upgrade I used her iPod to backup her files that she still needed. After installing Ubuntu I wanted to copy these files back to the computers hard drive. 

Ubuntu mounts the iPod after I plug it into the USB port. There is a fancy iPod icon on the desktop. I can open up Nautilus and browse the files on the iPod. When I try to copy the files (or open directly from the iPod) to the home directory the file transfer errors out:

**********
"Error "I/O error" while copying "/media/NE...filename".

Would you like to continue?
Skip|Cancel|Retry
**********

At this time the iPod is automatically unmounted and the desktop icon disappears. 

The iPod itself seems fine. I was able to connect it to my laptop (Win XP) and copy the files to a thumbdrive. How do I begin to troubleshoot this issue? What would cause Ubuntu to unmount the iPod?

Thanks!

---

### Post by pjman on 2007-05-07
Anyone?

---

### Post by pjman on 2007-05-09
Here are some log files that I found. Ideas anyone?

/var/log/messages

```

[   81.186626] usb 4-2: new high speed USB device using ehci_hcd and address 3
[   81.319663] usb 4-2: configuration #1 chosen from 1 choice
[   81.320018] scsi1 : SCSI emulation for USB Mass Storage devices
[   86.323066] scsi 1:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[   86.326962] SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
[   86.327854] sdb: Write Protect is off
[   86.329474] SCSI device sdb: 39063023 512-byte hdwr sectors (20000 MB)
[   86.330351] sdb: Write Protect is off
[   86.330362]  sdb: sdb1 sdb2
[   86.401917] sd 1:0:0:0: Attached scsi removable disk sdb
[   86.402002] sd 1:0:0:0: Attached scsi generic sg1 type 0
[  102.963876] usb 4-2: reset high speed USB device using ehci_hcd and address 3
[  133.204025] usb 4-2: reset high speed USB device using ehci_hcd and address 3
[  143.446733] usb 4-2: reset high speed USB device using ehci_hcd and address 3
[  159.792681] usb 4-2: reset high speed USB device using ehci_hcd and address 3
[  160.040649] usb 4-2: reset high speed USB device using ehci_hcd and address 3
[  170.283313] usb 4-2: reset high speed USB device using ehci_hcd and address 3
[  170.416509] sd 1:0:0:0: scsi: Device offlined - not ready after error recovery
[  170.416532] sd 1:0:0:0: SCSI error: return code = 0x00050000
[  170.416536] end_request: I/O error, dev sdb, sector 11072029
[  170.416595] lost page write due to I/O error on sdb2
[  170.416610] lost page write due to I/O error on sdb2
[  170.416625] lost page write due to I/O error on sdb2
[  170.416633] lost page write due to I/O error on sdb2
[  170.416646] lost page write due to I/O error on sdb2
[  170.416654] lost page write due to I/O error on sdb2
[  170.416661] lost page write due to I/O error on sdb2
[  170.416668] lost page write due to I/O error on sdb2
[  176.519551] lost page write due to I/O error on sdb2
[  176.519567] lost page write due to I/O error on sdb2
[  210.206268] usb 4-2: USB disconnect, address 3


```

/var/log/dmesg

```

[   26.397583] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   26.567620] usb 1-1: configuration #1 chosen from 1 choice
[   26.572573] hub 1-1:1.0: USB hub found
[   26.574518] hub 1-1:1.0: 3 ports detected
[   26.845607] hdc: LTN526D, ATAPI CD/DVD-ROM drive
[   26.887371] usb 1-1.1: new full speed USB device using uhci_hcd and address 4
[   27.031437] usb 1-1.1: configuration #1 chosen from 1 choice
[   27.247224] usb 1-1.2: new full speed USB device using uhci_hcd and address 5
[   27.392287] usb 1-1.2: configuration #1 chosen from 1 choice
[   27.599068] usb 1-1.3: new full speed USB device using uhci_hcd and address 6
[   27.629510] hdd: PLEXTOR CD-R PX-W1210A, ATAPI CD/DVD-ROM drive
[   27.685829] ide1 at 0x170-0x177,0x376 on irq 15
[   27.697154] SCSI subsystem initialized
[   27.704343] libata version 2.20 loaded.
[   27.716512] hda: max request size: 128KiB
[   27.724969] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   27.724982] hda: cache flushes not supported
[   27.725065]  hda: hda1 hda2 <<6>usb 1-1.3: configuration #1 chosen from 1 choice
[   27.768828] usbcore: registered new interface driver libusual
[   27.775215] Initializing USB Mass Storage driver...
[   27.779032]  hda5 >
[   27.779760] hdb: max request size: 128KiB
[   27.785634] hdb: 8421840 sectors (4311 MB) w/256KiB Cache, CHS=8912/15/63, UDMA(66)
[   27.785646] hdb: cache flushes not supported
[   27.785710]  hdb:<6>scsi0 : SCSI emulation for USB Mass Storage devices
[   27.786890] usbcore: registered new interface driver usb-storage
[   27.786896] USB Mass Storage support registered.
[   27.787045] usb-storage: device found at 6
[   27.787049] usb-storage: waiting for device to settle before scanning
[   27.820845]  hdb1
[   27.832704] hdc: ATAPI 52X CD-ROM drive, 120kB Cache, UDMA(33)
[   27.832717] Uniform CD-ROM driver Revision: 3.20
[   27.872893] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   28.354832] Attempting manual resume
[   28.354838] swsusp: Resume From Partition 3:5
[   28.354841] PM: Checking swsusp image.
[   28.355024] PM: Resume from disk failed.
[   28.390346] kjournald starting.  Commit interval 5 seconds
[   28.390365] EXT3-fs: mounted filesystem with ordered data mode.
[   32.836978] usb-storage: device scan complete
[   32.983904] scsi 0:0:0:0: Direct-Access     OEI-USB  CF/SM/SD/MS       2.4 PQ: 0 ANSI: 0

```

Thanks!

---

### Post by pjman on 2007-05-15
I'm sorry for all the "bumps"... It's been over a week and I'd really like to get this fixed for my sister.

Is there anyone out there that has any suggestions?

---

### Post by pjman on 2007-05-20
I've ruled out the possibility of the iPod being the problem. The same thing happens with a different iPod (same model).

Here's a really odd twist to this situation. The iPod works fine under the Live CD!!!!? What could be different between the Live CD and the actual install?


I'm begging for help here :-)

---

### Post by PriceChild on 2007-05-20
new thread: [http://ubuntuforums.org/showthread.php?t=449562](http://ubuntuforums.org/showthread.php?t=449562)

*closed*

---

