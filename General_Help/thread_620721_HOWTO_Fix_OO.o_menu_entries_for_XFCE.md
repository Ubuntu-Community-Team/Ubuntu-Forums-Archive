---
title: "HOWTO: Fix OO.o menu entries for XFCE"
date: 2007-11-22
forum: General Help
---

### Post by regeya on 2007-11-22
If you're tired of trying to start up OO.o Writer in XFCE and getting the OO.o shell instead, this is for you.

This should work for XFCE and any other environment that uses the standard /usr/share/applications dir.

type in 

sudo -s 

from terminal to get admin privs, then

cd /usr/share/apps

to enter the applications menu entries.  

Take a look at, say, ooo-writer.desktop.

Look for a line which reads:

ooffice -writer %U

and change it to:

oowriter %U

For whatever reason, the command line switch isn't passed to oowriter when started from the xfce menu, but the convenience binaries in /usr/bin work just fine.

I plan to file a bug report, but not right now; here in USia, it's the end of a holiday, I'm off to bed, and I'm not looking forward to starting a flame war between Ubuntu and Debian OO.o and XFCE maintainers.:lolflag: For now, I'll just enjoy that I can start up OO.o apps from the XFCE menu!

Cheers!

---

