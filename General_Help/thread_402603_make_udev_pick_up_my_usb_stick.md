---
title: "make udev pick up my usb stick"
date: 2007-04-05
forum: General Help
---

### Post by mdew on 2007-04-05
I can manually mount the disk, but being a mythbox I need udev to automagically mount the disk, can anyone help?

```

dpkg --list | grep udev
ii  udev                                     093-0ubuntu18.0edgy2
cat /etc/fstab | grep sda
/dev/sda1       /usb            vfat    umask=0,rw,gid=1000,uid=1000 0 0


[306397.648652] usb 3-5: new high speed USB device using ehci_hcd and address 4
[306397.783290] usb 3-5: configuration #1 chosen from 1 choice
[306397.962452] scsi1 : SCSI emulation for USB Mass Storage devices
[306397.965701] usb-storage: device found at 4
[306397.965704] usb-storage: waiting for device to settle before scanning
[306402.950034] scsi 1:0:0:0: Direct-Access     USBDisk  RunDisk          1.00 PQ: 0 ANSI: 2
[306402.955367] SCSI device sda: 8020000 512-byte hdwr sectors (4106 MB)
[306402.955993] sda: Write Protect is off
[306402.955997] sda: Mode Sense: 0b 00 00 08
[306402.955998] sda: assuming drive cache: write through
[306402.958109] SCSI device sda: 8020000 512-byte hdwr sectors (4106 MB)
[306402.958729] sda: Write Protect is off
[306402.958733] sda: Mode Sense: 0b 00 00 08
[306402.958734] sda: assuming drive cache: write through
[306402.958740]  sda: sda1
[306403.110065] sd 1:0:0:0: Attached scsi removable disk sda
[306403.138745] sd 1:0:0:0: Attached scsi generic sg0 type 0
[306403.139203] usb-storage: device scan complete

```

---

