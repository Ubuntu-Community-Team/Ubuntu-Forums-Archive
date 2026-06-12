---
title: "[SOLVED] Scanner on all in 1 was not working when plugged into USB 3 port but printer"
date: 2014-01-20
forum: General Help
---

### Post by dallase1 on 2014-01-20
Anyone know why a All in one printers scanner function would not work in Ubuntu 12.04 (precise) 64-bit when plugged into a USB port but the printer function worked fine and the scanner worked fine through Windows XP running as a Virtual machine with VMware player but if it was plugged into a USB 2 port all functions worked just fine under Ubuntu 12.04 (precise) 64-bit.
I have a Samsung SCX 4623f all in one laser printer and all of asudden I could not use the scanner fiction of it in Ubuntu 12.04 (precise) 64-bit the program would detect the scanner as being present but when I would hit scanner it would sit ther for a bout 30 seconds the window on the scanning program would turn Gray as if it was hung and then get a error message saying it got a hardware I/O error but if I used Windows XP running in a Virtual Machine it would detect and access the scanner just fine.
I decided to see what would happen if I plugged it into a different Port that happened to be a USB 2 port instead of a USB 3 port and now it is working. Why would only Ubuntu have trouble accessing the scanner part of the printer when plugged into a USB 3 port but Windows running under a Virtual machine with Ubuntu as the host machine be able to access the printer?  If the host machine can't see the scanner properly then haw can anything running on the host operating system access the scanner?

The problem was it was hooked to a USB 3 port and for some reason only Linux could not access it on that port but Windows 7 and Windows XP running in a virtual session could.

---

