---
title: "Problems installing libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386"
date: 2012-12-26
forum: General Help
---

### Post by Mad-Halfling on 2012-12-26
Hi, I'm trying to get Steam running on my 64-bit 12.10 install, but I'm hitting some problems with dependencies.

It's wanting libgl1-mesa-dri:i386 but this depends on libdrm-intel1:i386 libdrm-nouveau2:i386 and libdrm-radeon1:i386, but those don't seem to want to install.  The errors I'm getting are:-

```
Unpacking libdrm-intel1:i386 (from .../libdrm-intel1_2.4.39-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-intel1_2.4.39-0ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libdrm-intel1/changelog.Debian.gz', which is different from other instances of package libdrm-intel1:i386
No apport report written because MaxReports has already been reached
                                                                    Unpacking libdrm-nouveau2:i386 (from .../libdrm-nouveau2_2.4.39-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libdrm-nouveau2/changelog.Debian.gz', which is different from other instances of package libdrm-nouveau2:i386
No apport report written because MaxReports has already been reached
                                                                    Unpacking libdrm-radeon1:i386 (from .../libdrm-radeon1_2.4.39-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libdrm-radeon1_2.4.39-0ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libdrm-radeon1/changelog.Debian.gz', which is different from other instances of package libdrm-radeon1:i386
No apport report written because MaxReports has already been reached
                                                                    Selecting previously unselected package libgl1-mesa-dri:i386.
Unpacking libgl1-mesa-dri:i386 (from .../libgl1-mesa-dri_9.0-0ubuntu1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libdrm-intel1_2.4.39-0ubuntu1_i386.deb
 /var/cache/apt/archives/libdrm-nouveau2_2.4.39-0ubuntu1_i386.deb
 /var/cache/apt/archives/libdrm-radeon1_2.4.39-0ubuntu1_i386.deb

```

I've checked in Synaptic and the 64 bit versions of the libdrm-* packages are installed and are 2.4.39, so I'm not sure why there's an issue.  Searching for this issue finds me a few bug reports, so it seems I'm not alone, but I was wondering if there were any work-arounds for this?

---

### Post by ResetReboot on 2013-01-26
I've got the same problem. The x64 version is installed, and to my understanding, the i386 should install along with multiarch, but dependencies collide. 

I tried doing ```
sudo dpkg -i --force-depends steam_latest.deb
``` and it install and works, so the dependency is not an issue, but apt-get says it's broken, so everytime I try to run an update, it removes the package.

¿Maybe we should edit the .deb and remove the dependency?

---

