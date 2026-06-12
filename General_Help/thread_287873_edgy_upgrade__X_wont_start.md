---
title: "edgy upgrade  X wont start"
date: 2006-10-29
forum: General Help
---

### Post by heathen on 2006-10-29
So i upgraded my 2 computers last night using
```
gksu "update-manager -c"
```
my desktop has come right up, everything appears to be fine
my laptop however will not load X, this is what i see after the bootsplash
```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux laptop 2.6.17-10-386 #2 Fri Oct 13
18:41:40 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 29 08:02:26 2006
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "i810" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found
```

What do I need to do to get my laptop working again?

---

### Post by Najand on 2006-10-29
Run:
```

sudo apt-get -f install xserver-xorg-video-i810

```
in the command line to install the neccessory drivers. And then try to start X again or restart your computer.

---

### Post by heathen on 2006-10-29
sweet, that worked.. thanks...

---

