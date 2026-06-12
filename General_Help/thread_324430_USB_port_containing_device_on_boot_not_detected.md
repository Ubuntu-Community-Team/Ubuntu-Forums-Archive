---
title: "USB port containing device on boot not detected"
date: 2006-12-23
forum: General Help
---

### Post by Scythe!? on 2006-12-23
Hi, I'm running on Edgy (6.10 stable) and I'm having a problem. I have a usb mouse and it is no longer working properly if it is plugged in during boot (works fine in windows & dapper). From reading the boot log, I can see that on the hub that the mouse is plugged into, only 3 out of 4 ports are detected. The missing port is the one with the mouse in. This undetected port doesn't work at all unless i reboot with the mouse in another port. However, any device is plugged in during boot. The port that contains the device does not work.

Anyway to fix this?
Many thanks

---

### Post by blackmh on 2006-12-23
Check in BIOS if USB devices support during boot is turned on. Also, on some (older i think) BIOSes there is PNP system option so check that as well. On the other hand, problem might be in USB hub/port, low voltage etc...

---

### Post by Scythe!? on 2006-12-24
USB is enabled during boot. The port is powered (mouse is on) until it detects all the ports, then the mouse and the port loses power.

---

### Post by KevinEldon on 2006-12-27
Was a fix ever found for this problem?  I'm having the same trouble.

---

### Post by KevinEldon on 2006-12-28
I found a fix that worked for me.  I edited the GRUB config file (/boot/grub/menu.1st) and passed 'noapic' to the kernel.  My USB devices were detected and began working properly.

---

### Post by derby007 on 2006-12-28
Hi, can u be a bit more specific as i have the same problem when upgrading from Dapper to Edgy, ie. what did u EDIT in menu.1st & what command did u use to pass to the kernel, thanks.

---

