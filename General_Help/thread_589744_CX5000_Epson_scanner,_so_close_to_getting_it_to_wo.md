---
title: "CX5000 Epson scanner, so close to getting it to work, help"
date: 2007-10-24
forum: General Help
---

### Post by Tucatts on 2007-10-24
Ok, I am SO close to getting this thing to work in Gutsy. Worked fine in Feisty so I know the scanner is fine. 
I go to terminal and put in sudo scanimage -L and my scanner beeps as it should and terminal shows the scanner, all good so far.
put in lsusb and again get the correct respionse
Bus 004 Device 004: ID 04b8 : 082b Seiko Epson Corp. and so forth.

here is the rub, when I put in sudo chmod 666 /proc/bus/usb/004/004 I get the following:
cannot access /proc/bus/usb/004/004 : no such file or directory.

I know this is a work around but it worked great in Feisty and would be fine until I rebooted. and suited my needs just fine. The above is exactly what I did in Feisty so what should I do different for Gutsy.
Any suggestions would be great. 
Thanks!

---

