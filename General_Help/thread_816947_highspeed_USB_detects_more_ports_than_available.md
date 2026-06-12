---
title: "highspeed USB detects more ports than available"
date: 2008-06-03
forum: General Help
---

### Post by dhap on 2008-06-03
While connecting a USB strage device to my IBM T42 machine with Ubuntu8.04, I found that the device was not recognised. This is what I got from dmesg

usb 4-4: new full speed USB device using ehci_hcd and address 4
usb 4-4: new full speed USB device using ehci_hcd and address 18
.
.

I noticed that the module is trying to find 4 usb ports while there are only 2 available. I removed the ehci_hcd module and kept only the low speed uhci_hcd. The usb devices were instantly recognised. 

 usb 2-2: new full speed USB device using uhci_hcd and address 4
 usb 2-2: configuration #1 chosen from 1 choice
 scsi9 : SCSI emulation for USB Mass Storage devices


I separately unloaded and loaded the uhci_hcd and ehci_hcd and checked the dmesg. This is what I get when uhci_hcd is loaded:

hub 3-0:1.0: 2 ports detected

and this for ehci_hcd:

hub 4-0:1.0: 6 ports detected

Why is there a difference in number of ports? Is this is what creating the problem with high speed usb? How do I solve it?

---

