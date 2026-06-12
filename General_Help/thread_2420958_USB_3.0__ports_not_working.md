---
title: "USB 3.0  ports not working"
date: 2019-06-13
forum: General Help
---

### Post by Joe_Linux on 2019-06-13
I am running Ubuntu 18.04.2
My main board is a GIGABYTE GA-78LMT-USB3
None of my USB 3.0 ports work (in the front of the case or on the main boards i/o area) or show up on command line lsusb
Went into bios enabled Onboard USB 3.0 Controllers
The following were enabled:
USB Controllers
USB Legacy Function 
USB Storage Function
The USB 3.0 ports were working just a short time ago
All my USB 2.0 ports work normally 


   Any help would be appreciated

---

### Post by Joe_Linux on 2019-06-14
bump

---

### Post by dino99 on 2019-06-14
you wrote "The USB 3.0 ports were working just a short time ago" 
does that mean "with 18.04.2" and with which kernel ?
have you tested with some other (older) kernels ?
which DE is used ? which kind of session ? (gnome-shell on org/wayland, kde, ...)
what is the output of "lsusb -t" ?
what is output of "journalctl -b | grep usb"

---

### Post by rbmorse on 2019-06-14
The information Dino requested would be helpful.  Please use code tags.

That motherboard is pretty old, dating back to around 2012.  The USB3.0 controller was not part of the AMD PCH chipset, rather it came from a third-party IC added by Gigabyte.  It is possible the chip simply failed.

---

