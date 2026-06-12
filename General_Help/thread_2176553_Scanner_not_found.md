---
title: "Scanner not found?"
date: 2013-09-24
forum: General Help
---

### Post by decrepit on 2013-09-24
I'm using 12.04 with an H P Deskjet 3520, Installed the printer/scanner several months ago and all worked fine.
Went to do a scan yesterday, and got the message, "no scanners found", tried the print function, that works fine.
Booted into windoze and it scans normally.

I tried doing ```
hp-setup
``` and that also reports "no devices found", but the printer works.

Can anybody help? I hate having to boot into windows.
Do I need to reinstall HPLIP?

---

### Post by decrepit on 2013-09-29
OK reinstall hplip, that's improved it, I can now do a "simple scan" but xsane "fails to start scanner" if I just hit the "scan" button. But if I preview first, it will scan the selected area.
Weird eh?

---

### Post by JKyleOKC on 2013-09-29
My scanners are Epson so I can't give any detailed help, but I had similar problems originally. Since they worked as expected via Windows, I simply installed VirtualBox, then created a virtual machine and installed my WinXP CD on it. After installing the Epson drivers into the VM and setting up VBox's USB filters to grab the scanner automatically at boot time, I have the best of both worlds. I can launch the VM without rebooting, and use the scanner from there. A bit roundabout, but better than having to reboot. The same approach should work for you.

---

