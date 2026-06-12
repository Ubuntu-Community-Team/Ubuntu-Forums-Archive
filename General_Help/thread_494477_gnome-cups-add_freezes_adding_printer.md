---
title: "gnome-cups-add freezes adding printer"
date: 2007-07-06
forum: General Help
---

### Post by gardenlevel on 2007-07-06
Hi, I've found a number of other posts with the same issue but no solutions that work for me.

When I try to add a printer by clicking the "New Printer" icon I get the "gnome-cups-add" pop up that says "Reading printer database..." but it freezes there.

I don't know what to try next. My printer is a Canon MP500 (USB). I've tried a fresh install of Feisty  and It freezes before and after I install the updates. I've taken the printer off a hub and connected it directly to the PC.

Please help.

---

### Post by dcstar on 2007-07-07
> **gardenlevel said:**
> Hi, I've found a number of other posts with the same issue but no solutions that work for me.

When I try to add a printer by clicking the "New Printer" icon I get the "gnome-cups-add" pop up that says "Reading printer database..." but it freezes there.

I don't know what to try next. My printer is a Canon MP500 (USB). I've tried a fresh install of Feisty  and It freezes before and after I install the updates. I've taken the printer off a hub and connected it directly to the PC.

Please help.

Make sure you have both the **gnome-cups-manager** & **system-config-printer** packages installed, you then get two menu items for setting up printers and if one doesn't work, the other does (in my experience).

---

### Post by gardenlevel on 2007-07-12
Thanks for the advice, but neither work... They both just freeze.

Another symptom I noticed is xsane seems to be messed up. When I start xsane it freezes at scanning for devices. I tried removing all devices and it still doesn't work, so I don't think its my printer/scanner. I've tried different USB ports, none of them work. In fact, if I boot into XP or OpenSUSE, they both see my printer and scanner. The scanner works fine in both but I need to find drivers for printing in SUSE. I don't like SUSE, I'd rather use Ubuntu, but I may not be able too.

This seems to be a problem unique to Ubuntu, not Linux in general. I'm guessing its a bug, and I'm betting I'm not the only one affected, but how do I get enough information to file a bug report?

---

### Post by gardenlevel on 2007-07-13
OK, more info.

If I run this: *cat /var/log/messages | grep par *

I get this:

Jul 13 14:09:33 dave-desktop kernel: [ 7215.998548] usb 3-1.4: new high speed USB device using ehci_hcd and address 108
Jul 13 14:09:33 dave-desktop kernel: [ 7216.092800] usb 3-1.4: configuration #1 chosen from 1 choice
Jul 13 14:09:33 dave-desktop kernel: [ 7216.094378] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 108 if 1 alt 0 proto 2 vid 0x04A9 pid 0x170C
Jul 13 14:09:33 dave-desktop kernel: [ 7216.094502] scsi9 : SCSI emulation for USB Mass Storage devices
Jul 13 14:09:38 dave-desktop kernel: [ 7221.093845] scsi 9:0:0:0: Direct-Access     Canon    MP500Storage     0109 PQ: 0 ANSI: 2
Jul 13 14:09:38 dave-desktop kernel: [ 7221.107044] sd 9:0:0:0: Attached scsi removable disk sde
Jul 13 14:09:38 dave-desktop kernel: [ 7221.107080] sd 9:0:0:0: Attached scsi generic sg4 type 0

So it DOES see my printer.

If I run this: *lpinfo -v* I get nothing, it just freezes

I've attached my cups error log.

---

