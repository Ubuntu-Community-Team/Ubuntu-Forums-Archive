---
title: "[SOLVED] HP OfficeJet G55 - installs, doesn't print"
date: 2007-08-31
forum: General Help
---

### Post by kerryhall on 2007-08-31
Hey all.

I have an HP OfficeJet G55 (connected through usb) that installs fine, is autodetected and everything. However, when I send a job to it, it doesn't respond. It just says "open print channel failed" It is the most maddening thing ever. I am running Edgy desktop, and the printer driver is hpijs.

Thanks!

---

### Post by tgalati4 on 2007-09-01
Try a different USB cable or a different USB port.  Does the printer work in Windows?  HP's aren't known for their reliability.

Look in /var/log for any error messages.  Also check dmesg.

>dmesg | more

---

### Post by kerryhall on 2007-09-01
Simply rebooting the computer seems to have fixed it! Thanks!

---

