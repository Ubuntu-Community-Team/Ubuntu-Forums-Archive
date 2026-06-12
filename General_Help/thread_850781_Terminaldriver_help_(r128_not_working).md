---
title: "Terminal/driver help? (r128 not working)"
date: 2008-07-05
forum: General Help
---

### Post by Error 404 on 2008-07-05
Ok, I've installed Ubuntu 8.04 onto my laptop, but the display driver isn't working. I've installed the package, but it hasn't done anything.
From some research, it appears I'm meant to modify the xorg.conf file, but I dont know how.:confused:
So, I need to open the file and at the same time have SUDO privalages.
How do I do this? Do I use terminal?
The graphics card I'm trying to get working is an ATi Rage 128 M3 on my Dell Inspiron 4000. Currently it is limited to 800 x 600 resolution.:(
Help?

---

### Post by oldos2er on 2008-07-06
To edit your xorg.conf file with admin privileges, type "gksudo gedit /etc/X11/xorg.conf" in a terminal.

---

### Post by Error 404 on 2008-07-06
Ok, I've done that and edited the xorg.conf file, but unfortunately it hasn't solved my driver problem...
How do I enable the r128 driver? It is obviously not working, otherwise I'd have a proper resolution on my screen...

---

### Post by overdrank on 2008-07-06
> **Error 404 said:**
> Ok, I've done that and edited the xorg.conf file, but unfortunately it hasn't solved my driver problem...
How do I enable the r128 driver? It is obviously not working, otherwise I'd have a proper resolution on my screen...

Hi and did you try what I suggested in your other thread 
[http://ubuntuforums.org/showthread.php?p=5323501#post5323501](http://ubuntuforums.org/showthread.php?p=5323501#post5323501)

---

