---
title: "esetroot"
date: 2015-01-29
forum: General Help
---

### Post by nep-nori on 2015-01-29
So while reading about Fluxbox and its fancy pseudo-transparency, it seems windows will only display the wall behind them if said wall was set by feh, esetroot or wmsetbg.

It is said in the same page that esetroot comes packaged as part of eterm, but reading its package details [here]("http://packages.ubuntu.com/trusty/eterm") esetroot is nowhere to be seen. Can anyone enlighten me?

---

### Post by vasa1 on 2015-01-29
Can't enlighten you but here's a link: [http://www.linux-magazine.com/Issues/2005/53/DeskTOPia-hsetroot-Esetroot](http://www.linux-magazine.com/Issues/2005/53/DeskTOPia-hsetroot-Esetroot)

I use hsetroot on Openbox. Won't that work for you? Also look at the output of *apt-cache show gsetroot*:
```
10:57 PM ~ $ acsh gsetroot
Package: gsetroot
Priority: extra
Section: universe/utils
Installed-Size: 85
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: amd64
Version: 1.1-3
Depends: libatk1.0-0 (>= 1.12.4), libc6 (>= 2.3.4), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.8.0), eterm
Filename: pool/universe/g/gsetroot/gsetroot_1.1-3_amd64.deb
Size: 14266
MD5sum: 469dbe071697243d1a2b0a3cb39ad6e8
SHA1: f2b72f60fb8a42188ab47fdc1d5af9bb30b8182e
SHA256: 6d8534558545edbacacec18179008e1afbd6f3b74144ed0a0df44c65cd5baf77
Description-en: grahical GTK-based front-end for Esetroot
 It can be used to choose a wallpaper and configure root window.
 It works under Window Managers like FluxBox, Enlightenment, WindowMaker
 NextStep, BlackBox, IceWM and others...
 This software is under the GPL license.
Description-md5: 650bcad84b6b1bbc0522eaf74d32f5b5
Homepage: http://freecode.com/projects/gsetroot
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

---

