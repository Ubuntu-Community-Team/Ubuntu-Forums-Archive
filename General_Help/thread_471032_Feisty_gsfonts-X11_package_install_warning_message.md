---
title: "Feisty gsfonts-X11 package install warning messages"
date: 2007-06-11
forum: General Help
---

### Post by mattengland on 2007-06-11
I experienced these warning messages when install gsfonts-X11 on a fresh Feisty install (in order to get Opera-Flash display fonts to work properly on ESPN.com's Spotlight view).

Any thoughts on if these symptoms are benign, and if not, what I should do to fix it?  (The install did fix the Opera-espn.com view problem.)

```
root@matts-laptop:~# apt-get install gsfonts-x11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gsfonts-x11
0 upgraded, 1 newly installed, 0 to remove and 46 not upgraded.
Need to get 10.6kB of archives.
After unpacking 119kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com feisty/main gsfonts-x11 0.20build1 [10.6kB]
Fetched 10.6kB in 0s (16.2kB/s)
Selecting previously deselected package gsfonts-x11.
(Reading database ... 88299 files and directories currently installed.)
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.20build1_all.deb) ...
Setting up gsfonts-x11 (0.20build1) ...
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

root@matts-laptop:~# dir /usr/lib/X11/
config  rgb.txt  x11perfcomp  xsm
root@matts-laptop:~#
```

---

