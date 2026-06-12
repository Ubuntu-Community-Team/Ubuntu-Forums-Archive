---
title: "kubuntu 14.04 fresh install will not start"
date: 2014-07-03
forum: General Help
---

### Post by rudokf on 2014-07-03
Hi, all

My son just installed kubuntu 14.04 alongside windows on an older   Toshiba Tecra A6 laptop. kubuntu refuses to start after installation.
I get logo up and nothing else happens. Pressing ESC gets me to the status page. Last entry is "cup-browsed".
I can not get console up by pressing ALT-CTRL-F1 or any other   combination. Screen switches, but seems that kubuntu does not boot to   the point where login is displayed.

Tried to boot into recovery mode. Enabling networking in recovery mode   does not have proper setup for DNS, (there is no /etc/resolv.conf).   While it is annoying, it is easily fixable.
I then tried to do an update/upgrade and successfuly run an upgrade,   hoping some package upgrade will help, but that did not help my issue.
Reading the web, I found few references to possible issue with AMD   graphics driver. While I do not beleive it is the case, I tried to   unistall fglrx and found it was not installed. I then decided to try and   install it.
apt-get install fglrx eventually starts asking for a kubuntu 14.04 CD.   Something along the lines "Media change. Put a kubuntu 14.04 disk into   /cdrom/ and press enter". In recovery mode, there are no mount points   for cdrom and no /dev/ entry for a device either, so it is quite   problematic feeding it a disk.

Anyway, if anyone can help, this will be much appreciated!

Thanks,
Rudolf

---

### Post by xc3RnbFO8P on 2014-07-03
Did you use cable when installing Kubuntu?

---

