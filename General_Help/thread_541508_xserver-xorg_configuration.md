---
title: "xserver-xorg configuration"
date: 2007-09-02
forum: General Help
---

### Post by InGunsWeTrust on 2007-09-02
I am attempting to install gnome on a server so i can have a GUI on my server and I am having a slight problem trying to configure xserver-xorg. If I run the Ubuntu Live CD the x server runs just fine so this prompts me to think that there is some way to automatically configure xserver-xorg. Is there any way to do the same thing the Live CD does to just automatically run the configuration because there is no way I know all the answers to that thing.

---

### Post by tzulberti on 2007-09-02
You could run the live cd, and backup the file at /etc/X11/xorg.conf. Then, replace the xorg.conf in the installed partition with the one backup up..

You could also runs "sudo dpkg-reconfigure xserver-xorg", and a wizard will apears to configure xorg... I recommend this last option.

---

