---
title: "Problems with Card-Reader"
date: 2007-02-18
forum: General Help
---

### Post by quark13 on 2007-02-18
Hello,

I'm trying to get a MS-Tech Card-Reader to work on my Ubuntu 6.06 installation. I thought it should normally work right out of the box, but it isn't :(

My problem is, that i couldn't use the card reader, but the lights are happily flashing, whatever if a card is inserted or not. A cable / controller problem is in my opinion not possible, because the reader works fine under vista / xp. The only sign of live I get is a output in /var/log/syslog

Feb 18 12:24:16 localhost syslogd 1.4.1#17ubuntu7: restart.
Feb 18 12:24:16 localhost anacron[4642]: Job `cron.daily' terminated
Feb 18 12:24:16 localhost anacron[4642]: Normal exit (1 job run)
Feb 18 12:24:17 localhost kernel: [17180075.748000] usb 4-4: new high speed USB
device using ehci_hcd and address 122
Feb 18 12:24:18 localhost kernel: [17180076.504000] usb 4-4: new high speed USB
device using ehci_hcd and address 124
Feb 18 12:24:19 localhost kernel: [17180077.260000] usb 4-4: new high speed USB
device using ehci_hcd and address 126
Feb 18 12:24:19 localhost kernel: [17180077.764000] usb 4-4: new high speed USB
device using ehci_hcd and address 127
Feb 18 12:24:23 localhost kernel: [17180081.796000] usb 4-4: new high speed USB
device using ehci_hcd and address 16

this kernel message returns and returns untill unplugging the device from mainboard...

"lsusb" doesn't detect anything than my mouse, with "lspci" I get no information about the chipset, which is a "Alcor Micro Chipset", so I doesn't know where to start to get this reader working...

I've seen several threads in this forum where this chipset is automatically seen by ubuntu, so what could I do?

Thx for replies

---

