---
title: "[SOLVED] 7.10 APT-GET issues"
date: 2007-11-21
forum: General Help
---

### Post by wingmoto on 2007-11-21
I have upgraded from version 6.06 server to version 7.10 of ubuntu.  I have been trying to set up my server reconfigured and do some updates.  I have been trying to apt-get some graphic utilities and it is telling me that the files are no longer available:

Depends: libfreetype6 (>= 2.3.5) but it is not installable
                  Depends: libgraphicsmagick1 but it is not going to be installed
                  Depends: libice6 (>= 1:1.0.0) but it is not installable
                  Depends: libjasper1 (>= 1.900.1) but it is not installable
                  Depends: libjpeg62 but it is not installable
                  Depends: liblcms1 (>= 1.15-1) but it is not installable
                  Depends: libsm6 but it is not installable
                  Depends: libtiff4 but it is not installable
                  Depends: libwmf0.2-7 (>= 0.2.8.4) but it is not installable
                  Depends: libx11-6 but it is not installable

The one I am trying to install is ImageMagick, which then directs me to graphicsmagic and ultimately getting the error above.  I have tried to install other graphic conversion utilities to run on my server with the same issues.  I have also tried to install the source versions, but I can't get any compilers installed due to the BINUTILS not being available anymore.  

I am guessing that there is something else at play here.  Apache runs great and I have everything else functioning as desired.  It is just this component(s) I am having issues with.  I am testing Yappa-NG and Gallery2 servers.  Any help is appreciated.  

Thanks in advance.

Matt White

---

### Post by aysiu on 2007-11-22
It sounds as if you have conflicting repositories. [Get a fresh sources.list](http://psychocats.net/ubuntu/sources#key) and try again: ```
sudo apt-get update
sudo apt-get -f install
sudo apt-get install imagemagick
```

---

### Post by wingmoto on 2007-11-22
This worked!  Thank you for the quick reply!

---

