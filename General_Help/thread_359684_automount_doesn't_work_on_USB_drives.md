---
title: "automount doesn't work on USB drives"
date: 2007-02-12
forum: General Help
---

### Post by ashrack on 2007-02-12
USB THUMB Drive doesn't get automounted.
This is the log from 
```
tail -f /var/log/messages/
```
```
Feb 12 14:47:58 tomi kernel: usb 3-3: new full speed USB device using ohci_hcd and address 3
Feb 12 14:47:59 tomi kernel: usb 3-3: configuration #1 chosen from 1 choice
Feb 12 14:47:59 tomi kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Feb 12 14:48:04 tomi kernel: scsi 0:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
Feb 12 14:48:04 tomi kernel: SCSI device sda: 960512 512-byte hdwr sectors (492 MB)
Feb 12 14:48:04 tomi kernel: sda: Write Protect is off
Feb 12 14:48:04 tomi kernel: SCSI device sda: 960512 512-byte hdwr sectors (492 MB)
Feb 12 14:48:04 tomi kernel: sda: Write Protect is off
Feb 12 14:48:04 tomi kernel:  sda: sda1
Feb 12 14:48:04 tomi kernel: sd 0:0:0:0: Attached scsi removable disk sda
Feb 12 14:52:29 tomi kernel: usb 3-3: USB disconnect, address 3

```

I attach the KDE error:
[ATTACH]25117[/ATTACH]

ps. I can still mount it manually

---

### Post by ashrack on 2007-02-13
bump

---

