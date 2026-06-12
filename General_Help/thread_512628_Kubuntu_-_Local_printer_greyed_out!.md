---
title: "Kubuntu - Local printer greyed out!"
date: 2007-07-29
forum: General Help
---

### Post by daller on 2007-07-29
Hi there,

I'm trying to setup a supported printer (parallel) on a Kubuntu 7.04 machine.

When I go into the printer utility (in system settings) the "Local printer" option is greyed out.

Cupsys is running, and the virtual parallel port is working:

dmesg: 

[22330.608000] usb 2-4: new full speed USB device using ohci_hcd and address 19
[22330.820000] usb 2-4: configuration #1 chosen from 1 choice
[22330.896000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 19 if 0 alt 1 proto 2 vid 0x067B pid 0x2305

lsusb:

Bus 002 Device 019: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port

What can I do to install the printer?

---

### Post by TBerben on 2007-07-30
Are you in the allowed/denied users list that CUPS maintains? CUPS´ default behaviour allows all users to access a printer, but maybe you (accidentally) restricted acces?

---

