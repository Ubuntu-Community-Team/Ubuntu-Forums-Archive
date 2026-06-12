---
title: "Irulu X10 tablet - misidentified"
date: 2023-04-26
forum: General Help
---

### Post by grey1beard on 2023-04-26
In trying to make use of an old Android tablet, an Irulu X10, I thought I'd explore the possibility of changing the OS to Ubuntu touch.

I've installed Hardinfo on my desktop(running Ubuntu 22.04) and when connecting the tablet to it via a usb cable, somewhat surprised to see it identified as **HTC (High Tech Computer Corp.) Android Phone (Fairphone First Edition (FP1))**.
Not making much headway with trying to unlock the bootloader, so I thought I should ask if anyone can shed light on this misidentification, first.

John
EDIT I've used terminal, lsusb, and that also gives the same, HTC (High Tech Computer Corp.) Android Phone (Fairphone First Edition (FP1) identity.

---

### Post by Holger_Gehrke on 2023-04-26
'lsusb' should give you two hexadecimal ID numbers: the Vendor ID and the device id. In the short output (without -v) they're written as one ID, four digits, a colon and another four digits. If you search for those in the USB id database /usr/share/misc/usb.ids (or online) you'll find that Irulu isn't in the db. And you'll probably find that the ID you've been given is listed as HTC Fairphone ... 

This is either a mistake in the db or more likely a fly-by-night company not spending any money on getting IDs of their own and using one that was already assigned at the time (Fairphone First Edition came out in 2013, Irulu X10 in 2014). On the other hand, AFAIK the Fairphone wasn't a product of HTC (Taiwanese, I believe) - it was made by A'Hong / Changhong (Mainland China, started out producing electronics for the military ...) for Fairphone B.V., so an error in the db isn't impossible. 

If the ID you get is 0bb4:0c03, then that's the one usb.ids has for the HTC Fairphone First Edition ...

Holger

---

### Post by grey1beard on 2023-04-26
Thanks for the in-depth analysis. I really appreciate it.
I'll get everything hooked up again, and report back here.
John

---

### Post by grey1beard on 2023-04-26
Here you are, the ID for the HTC phone, as you thought !
**Bus 003 Device 033: ID 0bb4:0c03 HTC (High Tech Computer Corp.) Android Phone [Fairphone First Edition (FP1)]**

---

