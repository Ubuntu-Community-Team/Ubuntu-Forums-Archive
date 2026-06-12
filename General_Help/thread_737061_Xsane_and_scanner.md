---
title: "Xsane and scanner"
date: 2008-03-27
forum: General Help
---

### Post by Dragyn55 on 2008-03-27
I've been using an Epson V200 Photo scanner on Hardy for a while now and everything was fine. But now Xsane can't detect the scanner unless I run it as root. Also if I run  scanimage -L in a terminal it doesn't see the scanner but if I run it as sudo  scanimage -L it does. Any ideas would be greatly appreciated. 

Michael

---

### Post by Dragyn55 on 2008-03-27
Never mind. I took the scanner drivers out completely. Then reinstalled them. Everything worked fine after restarting the computer.

Thanks anyways.

Michael

---

### Post by robc02 on 2008-04-27
How did you install your scanner on Hardy? Mine was working fine on Gutsy, but when I tried to install it on Hardy I found there was no /etc/udev/rules.d/45-libsane.rules file. I had already installed the iscan driver and plugin, but cannot tell teh system that the scanner exists (I presume thiat is what the 45-libsane-rules file does).

scanimage -L does not show the scanner, even with sudo. 
lsusb does show it.

Any help will be greatly appreciated.

---

