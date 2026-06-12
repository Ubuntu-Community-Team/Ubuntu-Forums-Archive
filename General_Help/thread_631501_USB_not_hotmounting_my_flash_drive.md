---
title: "USB not hotmounting my flash drive"
date: 2007-12-04
forum: General Help
---

### Post by t0ksik on 2007-12-04
My USB drives aren't automounting

CDs and DVDs work fine but nothing USB does.

I think the problem might have been caused by me because I accidentally unchecked the dbus service then I had whole bunch of trouble with HAL until I rechecked the dbus service.  Then I had to rename the dbus service in init.d to S12dbus because it defaulted by S50dbus and so it was starting after HAL.

This is  the result from a dmesg.  Also, could someone tell me what number dbus is supposed to be in the init.d folder?  Is it 12?  is HAL 12? I just guessed

```
[ 4033.644000] usb 4-1: new full speed USB device using ohci_hcd and address 5
[ 4033.864000] usb 4-1: configuration #1 chosen from 1 choice
[ 4033.888000] scsi13 : SCSI emulation for USB Mass Storage devices
[ 4033.888000] usb-storage: device found at 5
[ 4033.888000] usb-storage: waiting for device to settle before scanning
[ 4038.888000] usb-storage: device scan complete
[ 4038.892000] scsi 13:0:0:0: Direct-Access     Samsung  Mass Storage     age  PQ: 0 ANSI: 2
[ 4038.900000] scsi 13:0:0:1: Direct-Access     Samsung  Mass Storage     age  PQ: 0 ANSI: 2
[ 4038.920000] sd 13:0:0:0: [sdb] 32596 512-byte hardware sectors (17 MB)
[ 4038.924000] sd 13:0:0:0: [sdb] Write Protect is off
[ 4038.924000] sd 13:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 4038.924000] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 4038.944000] sd 13:0:0:0: [sdb] 32596 512-byte hardware sectors (17 MB)
[ 4038.948000] sd 13:0:0:0: [sdb] Write Protect is off
[ 4038.948000] sd 13:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 4038.948000] sd 13:0:0:0: [sdb] Assuming drive cache: write through
[ 4038.948000]  sdb:
[ 4038.964000] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 4038.964000] sd 13:0:0:0: Attached scsi generic sg1 type 0
[ 4038.976000] sd 13:0:0:1: [sdc] 3970049 512-byte hardware sectors (2033 MB)
[ 4038.980000] sd 13:0:0:1: [sdc] Write Protect is off
[ 4038.980000] sd 13:0:0:1: [sdc] Mode Sense: 0b 00 00 08
[ 4038.980000] sd 13:0:0:1: [sdc] Assuming drive cache: write through
[ 4039.000000] sd 13:0:0:1: [sdc] 3970049 512-byte hardware sectors (2033 MB)
[ 4039.004000] sd 13:0:0:1: [sdc] Write Protect is off
[ 4039.004000] sd 13:0:0:1: [sdc] Mode Sense: 0b 00 00 08
[ 4039.004000] sd 13:0:0:1: [sdc] Assuming drive cache: write through
[ 4039.004000]  sdc: sdc1
[ 4039.024000] sd 13:0:0:1: [sdc] Attached SCSI removable disk
[ 4039.024000] sd 13:0:0:1: Attached scsi generic sg2 type 0
[ 4069.540000] usb 4-1: reset full speed USB device using ohci_hcd and address 5

```

---

