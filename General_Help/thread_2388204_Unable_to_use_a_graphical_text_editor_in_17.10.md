---
title: "Unable to use a graphical text editor in 17.10"
date: 2018-03-30
forum: General Help
---

### Post by bilekbp on 2018-03-30
Hello, I'm trying to get my scanner (Fujitsu Scansnap S1100) to work in Ubuntu 17.10. I need to enable the SANE backend for my scanner in /etc/sane.d/dll.conf according to the help article I've found. However, when running gksudo gedit I receive the following error:
(gedit: 32484): Gtk-WARNING **: cannot open display: :0.0
not connect: Connection refused

According to some other things I've read there may be an issue with Wayland? I'm quite confused, I'd just like to be able to run a graphical text editor to be able to add a simple line to the dll.conf file. Could someone assist me with this?

Thank you!

---

### Post by deadflowr on 2018-03-30
See if post #1 here:
[https://ubuntuforums.org/showthread.php?t=2375077]("https://ubuntuforums.org/showthread.php?t=2375077")
resolves the issues you see.

Then try running gksu gedit as you wish

---

