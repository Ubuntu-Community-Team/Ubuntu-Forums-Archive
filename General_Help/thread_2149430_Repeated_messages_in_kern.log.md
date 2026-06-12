---
title: "Repeated messages in kern.log"
date: 2013-05-28
forum: General Help
---

### Post by scbingham on 2013-05-28
Hello All, I have these messages repeated every minute in kern.log:

usb 1-6: reset high-speed USB device number 3 using ehci_hcd
sd 4:0:0:0: [sdb] Test WP failed, assume Write Enabled
sd 4:0:0:0: [sdb] Asking for cache data failed
sd 4:0:0:0: [sdb] Assuming drive cache: write

This appears to be the inbuilt card reader, which I use rarely & there's no card in it.

lsusb: 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 002: ID 0425:0001 Motorola Semiconductors HK, Ltd

Should I be concerned & how do I stop the errors appearing?

I'm running Ubuntu 12.04 LTS 64bit on an Advent 5301 laptop.

Thanks in advance for any assistance.

---

