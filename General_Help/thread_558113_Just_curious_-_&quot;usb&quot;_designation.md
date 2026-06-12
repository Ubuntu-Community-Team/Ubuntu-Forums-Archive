---
title: "Just curious - &quot;usb:&quot; designation"
date: 2007-09-23
forum: General Help
---

### Post by Junosix on 2007-09-23
Helped a friend hook up his Palm Pilot to Ubuntu yesterday, I notice that the pilot-xfer software talks to the Palm Pilot via a device file in this way:

usb:/dev/ttyUSB1

I understand the /dev/ttyUSB1 bit which points to the relevant device file, but what's the reason for having "usb:" in front of it? Is it a way for Linux to hit the USB ports directly, and is it something intrinsically hardwired to the kernel or is it closer to something like a symlink and you create your own "xxx:" device/port (not that I could think I'd ever need to)?

What other "xxx:" devices/ports are there?

---

### Post by geraldm on 2007-09-23
What other "xxx:" devices/ports are there?

scsi

The line is processed by software, so any option can be made available by the processing
program.   parallel port, ieee1394, etc.

Gerald

---

