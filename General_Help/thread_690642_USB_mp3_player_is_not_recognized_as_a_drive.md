---
title: "USB mp3 player is not recognized as a drive"
date: 2008-02-07
forum: General Help
---

### Post by ChAoS.ct on 2008-02-07
Hi all,

I just bought an mp3 player [palachan]("http://www.ciao.es/Toshiba_PALA_CHAN__755450"): 1 GB capacity USB connection, 13.80€ :)

lsusb:
```
Bus 005 Device 011: ID 0930:1401 Toshiba Corp. 
```

I tried to get itworking on Ubuntu with no success.
When I connect it on my USB:
dmesg:
```

[ 6347.605195] usb 5-4: new high speed USB device using ehci_hcd and address 11
[ 6347.749273] usb 5-4: configuration #1 chosen from 1 choice
[ 6347.752395] scsi9 : SCSI emulation for USB Mass Storage devices
[ 6347.754947] usb-storage: device found at 11
[ 6347.754959] usb-storage: waiting for device to settle before scanning
[ 6352.748288] usb-storage: device scan complete
[ 6352.749192] scsi 9:0:0:0: Direct-Access              Palachan USB MEM 1.06 PQ: 0 ANSI: 0 CCS
[ 6352.753035] sd 9:0:0:0: [sdd] 2002944 512-byte hardware sectors (1026 MB)
[ 6352.753841] sd 9:0:0:0: [sdd] Write Protect is off
[ 6352.753852] sd 9:0:0:0: [sdd] Mode Sense: 23 00 00 00
[ 6352.753857] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 6352.756915] sd 9:0:0:0: [sdd] 2002944 512-byte hardware sectors (1026 MB)
[ 6352.757677] sd 9:0:0:0: [sdd] Write Protect is off
[ 6352.757688] sd 9:0:0:0: [sdd] Mode Sense: 23 00 00 00
[ 6352.757692] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 6352.757702]  sdd: unknown partition table
[ 6352.761136] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[ 6352.761233] sd 9:0:0:0: Attached scsi generic sg4 type 0

```
And the device /dev/sdd is created, but not any /dev/sddX, so it does not recognizes the partitions on it.

I tried to format in Windows both in fat32 and fat(16) with no success.
I tried to create a new partition structure and format it in Ubuntu, no errors , but the result is the same.

The mp3 itself is working well and i can transfer files in Windows as well, but of course I want to use it in my laptop which only has Ubuntu.

Thanks in advance.

---

