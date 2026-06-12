---
title: "mount 5 inch external hard disk"
date: 2007-01-12
forum: General Help
---

### Post by daisycool on 2007-01-12
hi there,
i m new to Linux, i m using Ubuntu 6.10, and a 5 inch external hard disk  (200G desktop harddisk, with power supply)&#65292;there's always a failure.

When i turn on the hard disk, and plug it to the USB port, there's no obvious change on the desk top (no icon shows up), In the Hardware Manger, i can see there's a new device under the "USB mass storage interface", but the hardware name is not detected.

there was once, one of the partitions of the hard disk was mounted, and i could access it. but never happened again ....... i also found every time there's /dev/sda, or sometimes even more, like /dev/sda2, /dev/sda6, etc.

here i paste part of the 'dmesg'
......
......
[17182536.728000] usb 2-1: new high speed USB device using ehci_hcd and address 6
[17182536.860000] usb 2-1: configuration #1 chosen from 1 choice
[17182536.860000] scsi2 : SCSI emulation for USB Mass Storage devices
[17182536.860000] usb-storage: device found at 6
[17182536.860000] usb-storage: waiting for device to settle before scanning
[17182541.860000] usb-storage: device scan complete
[17182541.860000]   Vendor: Maxtor 6  Model: Y200P0            Rev: 0811
[17182541.860000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182541.864000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17182541.864000] sda: test WP failed, assume Write Enabled
[17182541.864000] sda: assuming drive cache: write through
[17182541.868000] SCSI device sda: 398297088 512-byte hdwr sectors (203928 MB)
[17182541.868000] sda: test WP failed, assume Write Enabled
[17182541.868000] sda: assuming drive cache: write through
[17182541.868000]  sda: sda1 sda2 < sda5 sda6 sda7 >
[17182541.932000] sd 2:0:0:0: Attached scsi disk sda
[17182541.932000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17182552.232000] sd 2:0:0:0: SCSI error: return code = 0x8000002
[17182552.232000] sda: Current: sense key: Hardware Error
[17182552.232000]     Additional sense: Data phase error
[17182552.232000] end_request: I/O error, dev sda, sector 103
[17182552.232000] printk: 1313 messages suppressed.
[17182552.232000] Buffer I/O error on device sda1, logical block 40


the whole message is quite long, i think this part might help. This is the end of message.

Thank you for your help!

cheers

---

