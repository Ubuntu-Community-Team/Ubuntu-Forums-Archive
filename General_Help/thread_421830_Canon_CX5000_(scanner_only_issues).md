---
title: "Canon CX5000 (scanner only issues)"
date: 2007-04-24
forum: General Help
---

### Post by profXavier on 2007-04-24
Hey ppl,

I am having an issue with scanning.  I had this same scanner working in Edgy, but in the past day or two, I moved to Feisty.

Here is some info:

lsusb
Bus 002 Device 006: ID 04b8:082b Seiko Epson Corp. 
Bus 002 Device 005: ID 05ac:120a Apple Computer, Inc. 
Bus 002 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 002: ID 046d:08f5 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

scanimage -d epson works
(I edited my /etc/sane.d/epson.conf to include this:
usb 0x4b8 0x82b
usb /dev/usbscanner0
)

When I open xsane (the app I want to use with my scanner), I see no devices (so it doesnt open at all). CLI give me no errors when I initialize xsane.

I realize the device can be communicated with, but xsane just doesnt find it.

One reason I think, is that I do not have a /dev/usbscanner0, but I do have a /dev/usblp0 (which i recall looking at during my previous install).

---

