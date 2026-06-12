---
title: "Installing MESA 7.0"
date: 2007-07-03
forum: General Help
---

### Post by aksdb on 2007-07-03
In order to get the radeon/ati driver to work with compiz-fusion, I wanted to install MESA 7.0. They compiled flawless (make linux-dri) and also the install seems to work (make install INSTALL_DIR=/usr DRI_DRIVER_INSTALL_DIR=/usr/lib/dri) but then glxinfo still reports MESA as being version 6.5.2. I even deleted all libGL* from /usr/lib which only resulted in glxinfo not running anymore (can't find the library), so it was at least trying to load the right one.
Any ideas what could be the cause of this problem? I don't want to fall back to fglrx/XGL :-(

---

