---
title: "Why vmware-player wants to remove other packages?"
date: 2007-03-04
forum: General Help
---

### Post by mloskot on 2007-03-04
Hi,

Could anyone explain me why when I try to install vmware-player under my Ubuntu 6.10 box, it wants to remove a lot of other packages, like **gnome-core** and many others?

Here is the screenshot from Synaptic:

[http://mateusz.loskot.net/tmp/vmware-removing-too-much.png]("http://mateusz.loskot.net/tmp/vmware-removing-too-much.png")

Thanks for enlightening me!

---

### Post by yabbadabbadont on 2007-03-04
```
/home/bubba $ aptitude show vmware-player
Package: vmware-player
State: not installed
Version: 1.0.2-2
Priority: optional
Section: multiverse/misc
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 32.1M
Depends: vmware-player-kernel-modules, libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libexpat1 (>=
         1.95.8), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.1), libglib2.0-0 (>= 2.8.0),
         libgtk2.0-0 (>= 2.8.0), libice6, libjpeg62, libpango1.0-0 (>= 1.10.1), libpng12-0 (>= 1.2.8rel), librsvg2-2 (>=
         2.9.5), libsm6, libssl0.9.7, libstdc++5 (>= 1:3.3.4-1), libx11-6, libxext6, libxft2 (> 2.1.1), libxi6, libxml2 (>=
         2.6.20), libxrender1, libxt6, libxtst6, zlib1g (>= 1:1.2.1)
PreDepends: debconf (>= 0.5) | debconf-2.0
**Conflicts: libdbus-1-2**
Description: Free virtual machine player from VMware
 The free VMware Player lets you run pre-built virtual machines on your desktop.  You can run multiple operating systems
 side-by-side, easing the process of software development, testing, and evaluation. 
 
 Virtual machines developed in VMware Workstation, ESX Server, or VMware Server can be run in VMware Player. 
 
 To run the VMware Player, just run /usr/bin/vmplayer from within X. 
 
 Note: You will also need the VMware Player kernel modules to run vmplayer. These can be built from source from
 vmware-player-kernel-source, or you can install a pre-built vmware-player-kernel-modules package for your kernel.

```
Apparently it conflicts with libdbus-1-2 with is required by all those other packages....  sounds like a screw-up to me.  You might check launchpad to see if a bug has been filed about it.

---

### Post by mloskot on 2007-03-04
> **yabbadabbadont said:**
> Apparently it conflicts with libdbus-1-2 with is required by all those other packages....  sounds like a screw-up to me.

Indeed, there is already a bug report:

[Bug #60611 - [edgy] wrong dependence (libdbus-1-2)?]("https://bugs.launchpad.net/ubuntu/+source/vmware-player/+bug/60611")

Hmm, that's bad.

I tried to install vmware-player from the official VMWare's package .tgz but it needs to rebuild modules. Unfortunately, I can not find kernel headers for current kernel from Ubuntu 6.10.
Nothing like kernel-headers-2.6.17

mloskot:~$ uname -a
Linux dog 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

---

### Post by yabbadabbadont on 2007-03-04
Install linux-headers-generic

See also:  [http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware-player+howto](http://www.ubuntuforums.org/showthread.php?t=84275&highlight=vmware-player+howto)

---

### Post by mloskot on 2007-03-04
I follows your suggestions and everything works well!
Big thanks!

---

