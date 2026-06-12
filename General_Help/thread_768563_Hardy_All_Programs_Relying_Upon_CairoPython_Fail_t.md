---
title: "Hardy: All Programs Relying Upon Cairo/Python Fail to Open"
date: 2008-04-26
forum: General Help
---

### Post by rjonesx on 2008-04-26
I am sure that there is some sort of compatability issue via the upgrade going on here, but not sure. Below is an example error I get from trying to run Update Manager. Similar errors occur with the vast majority of programs on my computer because most, in some way or another, depend upon Python/Cairo for 2D graphics.

Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

History:
1. I used Update Manager to upgrade from 7.10 to 8.04 with no errors shown.
2. This is an AMD64 Laptop, I am running the 64 bit version of Hardy.
3. I get the following errors when I try to reinstall anything related to Python or Cairo...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of python-cairo is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

4. I have tried switching Users to a new user, just in case it was a legacy hack from my old user that was competing. Same problems exist.
5. I cannot use the Crash Manager to detail or report issues because it crashes too.

Please help me, I am pretty desperate at this point. Thanks!

---

### Post by SOULRiDER on 2008-04-26
Just in case, install python-cairo and python-gtk2
```
sudo aptitude intall python-cairo python-gtk2
```

---

### Post by rjonesx on 2008-04-26
Both are already installed and the newest version according to apt-get install...

---

