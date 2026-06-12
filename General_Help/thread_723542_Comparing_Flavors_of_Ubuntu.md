---
title: "Comparing Flavors of Ubuntu"
date: 2008-03-13
forum: General Help
---

### Post by snorkytheweasel on 2008-03-13
Surprisingly, I didn't see a thorough reply in "search threads".

If performance is the main criteria, which is faster on a "fairly fast" computer: ubuntu or kubuntu?

What are the minimum hardware specs for "OK" performance using xbuntu?

My boss is crippled by Remonditis. Which GUI (Gnome, KDE, XCFE, etc.) will give the best performance on a server? I need the normal utilities and system programs, a good editor, a terminal, a brower, and such, but no games, edutaniment, multimedia, office programs - no fluff. 

Is there a distro which is concerned with being the best possible server (with GUI) - including DNS, DHCP, LAMP, and other server essentials?

---

### Post by ElijahLynn on 2008-03-13
I am relatively new but I believe Xubuntu will give you the best performance. XCFE.

---

### Post by kellemes on 2008-03-13
Well, there are about 350+ distro's out there and a lot are made for servers..
If you want Ubuntu you need to grap one of the server-additions for sure.. it's installs LAMP, DNS-server or whatever you select from the installer automagically, and if you need X you can simply do..
```
sudo apt-get install xubuntu-desktop
```
to get XFCE as a great desktop-manager, this instead of Gnome or KDE taking over your server.

Edit: Personally I wouldn't install X on a server, a server need to be stable as much as possible, and X isn't helping.

---

### Post by kuja on 2008-03-13
I would ........... 

Install from the server CD, and the, seeing as you _require_ a gui, maybe install fluxbox, xterm, xserver-xorg, xorg, and a browser. Start with a relatively bare system, only install what you need, and you won't be left with any fluff.

Running a GUI all the time will only eat up valuable memory that could probably be used for something else. KDE and GNOME are both the heavyweights on the block, Xubuntu somewhere in the medium area, and things like fluxbox, windowmaker, and icewm are generally considered to be lightweight.

---

### Post by aysiu on 2008-03-13
If you want the best performance, don't use a GUI on the server--that's Ubuntu's default for servers.

If you want a lightweight GUI, check out a window manager (IceWM, Fluxbox, Enlightenment) instead of a full desktop environment (KDE, Gnome, Xfce).

---

