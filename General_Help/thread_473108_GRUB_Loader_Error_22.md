---
title: "GRUB Loader Error 22?"
date: 2007-06-13
forum: General Help
---

### Post by trav110 on 2007-06-13
I've been dual booting between XP and Ubuntu 7.04 for a little while now, though I primarily run Windows. XP did an automatic update and restarted the computer while I was at work today, and now everytime I turn the computer on (after the logo disappears) all I see is the following:

GRUB Loader stage1.5

GRUB is now loading, please wait...
Error 22

No screen from which to choose operating systems, no nothing. Ubuntu is loaded onto an external HD that I've tried plugging into multiple different USB ports, but to no avail. I don't know what the hell is happening with my computer, and I'm ready to throw it out the window. Please help!

---

### Post by confused57 on 2007-06-13
> **trav110 said:**
> I've been dual booting between XP and Ubuntu 7.04 for a little while now, though I primarily run Windows. XP did an automatic update and restarted the computer while I was at work today, and now everytime I turn the computer on (after the logo disappears) all I see is the following:

GRUB Loader stage1.5

GRUB is now loading, please wait...
Error 22

No screen from which to choose operating systems, no nothing. Ubuntu is loaded onto an external HD that I've tried plugging into multiple different USB ports, but to no avail. I don't know what the hell is happening with my computer, and I'm ready to throw it out the window. Please help!
If you have a Window's install cd(not a recovery cd), you can restore Window's IPL to the internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

then if your bios is capable of booting first to USB, you might want to install grub to the external hard drive's mbr. using the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

boot first to your external drive & if you get a grub boot menu, highlight your Ubuntu entry, press "e", change root from (hd1,y) to (hd0,y), then press "b" to boot...

---

