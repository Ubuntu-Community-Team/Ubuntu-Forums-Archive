---
title: "after upgrade from edgy to feisty no mount external usb drives"
date: 2007-07-07
forum: General Help
---

### Post by wintermute12345 on 2007-07-07
hello communtiy,
today i've upgraded my edgy eft to feisty fawn using the internal release-upgrade (ist an mini server without X)

on edgy i had modified my fstab to mount three external discs at startup , there was anything fine, the 3 devices comes up from sda1 to sdc1

now on feisty , dmesg told me "bad filesystem" and also the manual mount fails with the same error, but if i type "dmesg" there will be list as follows:

[12519.912000] FAT: bogus number of reserved sectors
[12519.912000] VFS: Can't find a valid FAT filesystem on dev sda1.
[12519.932000] FAT: bogus number of reserved sectors
[12519.932000] VFS: Can't find a valid FAT filesystem on dev sdb1.
[12519.940000] FAT: bogus number of reserved sectors
[12519.940000] VFS: Can't find a valid FAT filesystem on dev sdc1.
[12678.588000] FAT: bogus number of reserved sectors
[12678.588000] VFS: Can't find a valid FAT filesystem on dev sda1.
[13063.500000] ehci_hcd 0000:00:10.3: remove, state 1
[13063.500000] usb usb4: USB disconnect, address 1
[13063.500000] usb 4-1: USB disconnect, address 2
[13063.508000] usb 4-2: USB disconnect, address 3
[13063.516000] usb 4-4: USB disconnect, address 4
[13063.516000] ehci_hcd 0000:00:10.3: USB bus 4 deregistered
[13063.516000] ACPI: PCI interrupt for device 0000:00:10.3 disabled
[13063.808000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[13063.976000] usb 2-2: configuration #1 chosen from 1 choice
[13063.976000] scsi5 : SCSI emulation for USB Mass Storage devices
[13063.976000] usb-storage: device found at 2
[13063.976000] usb-storage: waiting for device to settle before scanning
[13064.256000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[13064.412000] usb 1-1: configuration #1 chosen from 1 choice
[13064.416000] scsi6 : SCSI emulation for USB Mass Storage devices
[13064.416000] usb-storage: device found at 3
[13064.416000] usb-storage: waiting for device to settle before scanning
[13064.656000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[13066.920000] usb 1-2: configuration #1 chosen from 1 choice
[13066.924000] scsi7 : SCSI emulation for USB Mass Storage devices
[13066.924000] usb-storage: device found at 4
[13066.924000] usb-storage: waiting for device to settle before scanning
[13068.976000] usb-storage: device scan complete
[13068.980000] scsi 5:0:0:0: Direct-Access     ST330082 2A               0000 PQ: 0 ANSI: 0
[13068.988000] SCSI device sdd: 586072368 512-byte hdwr sectors (300069 MB)
[13068.992000] sdd: Write Protect is off
[13068.992000] sdd: Mode Sense: 27 00 00 00
[13068.992000] sdd: assuming drive cache: write through
[13069.000000] SCSI device sdd: 586072368 512-byte hdwr sectors (300069 MB)
[13069.004000] sdd: Write Protect is off
[13069.004000] sdd: Mode Sense: 27 00 00 00
[13069.004000] sdd: assuming drive cache: write through
[13069.004000]  sdd: sdd1
[13069.024000] sd 5:0:0:0: Attached scsi disk sdd
[13069.024000] sd 5:0:0:0: Attached scsi generic sg3 type 0
[13069.416000] usb-storage: device scan complete
[13069.420000] scsi 6:0:0:0: Direct-Access     WDC WD30 00JB-00KFA0      0811 PQ: 0 ANSI: 0
[13069.428000] SCSI device sde: 586072368 512-byte hdwr sectors (300069 MB)
[13069.432000] sde: test WP failed, assume Write Enabled
[13069.432000] sde: assuming drive cache: write through
[13069.440000] SCSI device sde: 586072368 512-byte hdwr sectors (300069 MB)
[13069.444000] sde: test WP failed, assume Write Enabled
[13069.444000] sde: assuming drive cache: write through
[13069.444000]  sde: sde1
[13069.452000] sd 6:0:0:0: Attached scsi disk sde
[13069.452000] sd 6:0:0:0: Attached scsi generic sg4 type 0

my question : how can mount these drives automatically at system startup ? 
remember, there is no monitor, tastatur, mouse or something else, only ssh command - line :-( 

thx 
wintermute

---

