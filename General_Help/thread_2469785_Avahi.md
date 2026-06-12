---
title: "Avahi"
date: 2021-12-09
forum: General Help
---

### Post by angel mike on 2021-12-09
I have read that there is a program called Avahi that could be blocking the download of the driver for the Brother Printer I have.

---

### Post by angel mike on 2021-12-09
This is the install messageduring downloading fromthe Brother website

 Preparing to unpack hl3150cdwlpr-1.1.2-1a.i386.deb ...
 Unpacking hl3150cdwlpr:i386 (1.1.2-1) over (1.1.2-1) ...
 Setting up hl3150cdwlpr:i386 (1.1.2-1) ...
 mkdir: cannot create directory ‘/var/spool/lpd/hl3150cdw’: No such file or directory
 chown: cannot access '/var/spool/lpd/hl3150cdw': No such file or directory
 chgrp: cannot access '/var/spool/lpd/hl3150cdw': No such file or directory
 chmod: cannot access '/var/spool/lpd/hl3150cdw': No such file or directory
 dpkg -i --force-all hl3150cdwcupswrapper-1.1.4-0a.i386.deb
 Selecting previously unselected package hl3150cdwcupswrapper:i386.
 (Reading database ... 191999 files and directories currently installed.)
 Preparing to unpack hl3150cdwcupswrapper-1.1.4-0a.i386.deb ...
 Unpacking hl3150cdwcupswrapper:i386 (1.1.4-0) ...
 Setting up hl3150cdwcupswrapper:i386 (1.1.4-0) ...
 Restarting cups (via systemctl): cups.service.
 lpadmin -p HL3150CDW -E -v usb://dev/usb/lp0 -P /usr/share/cups/model/Brother/brother_hl3150cdw_printer_en.ppd
 lpadmin: Printer drivers are deprecated and will stop working in a future version of CUPS.

---

### Post by Holger_Gehrke on 2021-12-09
I don't see how Avahi - a mDNS background process, somewhat comparable to Microsoft's ZeroConf or Apple's Bonjour - would influence a printer driver. I think this driver is simply OLD. Unless the package name is wrong it contains 32bit code - that's what i386 usually means. It also tries to use /var/spool/lpd/* - a directory structure used by the old lpd printing system which has been slowly replaced by CUPS in the last 20 years. And even it's integration with CUPS seems to use features which are on their way out ...

Holger

---

### Post by angel mike on 2021-12-09
Thanks Holger_Gehrke for that detailed reply - I will take it up with Brother technical dept.

---

### Post by angel mike on 2021-12-13
Have solved the problem - printer was not connected to a newly installed router. Will marked as solved.

---

