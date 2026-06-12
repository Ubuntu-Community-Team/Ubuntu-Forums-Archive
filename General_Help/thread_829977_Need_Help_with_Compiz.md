---
title: "Need Help with Compiz"
date: 2008-06-15
forum: General Help
---

### Post by jdtfk on 2008-06-15
Hi all, I'm new to this Ubuntu Movement so please take it easy on me =)
Used Compiz-check (saw it in another thread)
So here are the results:

juan@juan-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation GeForce 8800 GT (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems..../compiz-check: line 418: [: 1050: unary operator expected
./compiz-check: line 418: [: 1680: unary operator expected [ OK ]

As of yesterday everything worked as a charm, but then Update Manager told me to update, and I remember that there was an important update with xorg. I don't remember exactly the name of the update, if you could show me how to find a log of the updates installed, I could tell you exactly what it was. The thing is that today my effects are disabled, but I don't have troubles with drivers (as of Nvidia propietary ones). I want to get back my desktop effects =D

Thanks in advance.




EDIT: Nevermind, reinstalled the drivers and it worked back. =) If anyone has trouble with the latest xorg update, just reinstall your drivers.

---

### Post by Happy_Man on 2008-06-15
Yeah, a lot of people are having trouble with the Xorg update, and the solution seems to be to reinstall the restricted drivers.

---

