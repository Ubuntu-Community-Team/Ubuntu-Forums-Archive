---
title: "FireFox/Thunderbird printing always setting A4"
date: 2006-11-01
forum: General Help
---

### Post by KHatfull on 2006-11-01
Hi,

New Edgy install here, all going pretty much fine.

I've gotten a networked office printer here all setup in CUPS, can print test pages from both CUPS and the Gnome printing applet, all the OpenOffice.org apps print fine, however, every time I try to print out of Firefox or Thunderbird the printer errors out because the requested paper type is A4 and not Letter.

The printer in CUPS is set to US Letter, again all the OO apps print fine as well as test pages.  The printer is a Ricoh Aficio 1022 (for which there was a PPD already in CUPS) and it connects via socket on port 9100.

Any idea why the Mozilla apps seem to force A4 paper size?  When I go to the print dialog in Firefox and choose the printer properties the paper size shows up as Letter as it's defined in CUPS.

Any help appreciated, this is one of the last things to iron out before I install Edgy on a new desktop...I'm currently working on a play laptop.

Thanks!

---

### Post by Jorge on 2006-11-05
I am working on the same issue. I think it is a problem of the CUPS printing system, not related with a specific application. Look at this thread, it may help:

[http://www.ubuntuforums.org/showthread.php?t=78596](http://www.ubuntuforums.org/showthread.php?t=78596)

---

### Post by Jorge on 2006-11-09
Following other threads, I solved the issue in my system:

a) I edited the file /etc/paper, removed "a4" and wrote "Letter" (without quotes).
b) I removed and reinstall every printer.

---

