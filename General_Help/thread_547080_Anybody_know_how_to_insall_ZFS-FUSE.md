---
title: "Anybody know how to insall ZFS-FUSE?"
date: 2007-09-09
forum: General Help
---

### Post by shaggy999 on 2007-09-09
Has anyone had success installing the zfs-fuse beta? I'd like to try it out. I went to the project website and tried clicking a link to the source, but got no server response. So I used the following instructions for a debian install... which I thought might work with ubuntu since it's debian-based, but no dice.

Instructions:
Added the following repository to /etc/apt/sources.list
```
deb http://www.fushizen.net/zfs-fuse ./
```

Executed following commands:
```
sudo apt-get install devscripts build-essential zlib1g-dev libfuse-dev scons debhelper fakeroot
scons
dget http://www.fushizen.net/zfs-fuse/zfs-fuse_0.4.0~beta1.hg20070418.227.22a65c23850b-0~pre0.dsc
dpkg-source -x zfs-fuse_0.4.0~beta1.hg20070418.227.22a65c23850b-0~pre0.dsc
cd zfs-fuse-0.4.0~beta1.hg20070418.227.22a65c23850b
dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../zfs-fuse_0.4.0~beta1.hg20070418.227.22a65c23850b-0~pre0_*.deb
```

The dpkg-buildpackage command results in the following:
```
dpkg-buildpackage: source package is zfs-fuse
dpkg-buildpackage: source version is 0.4.0~beta1.hg20070418.227.22a65c23850b-0~pre0
dpkg-buildpackage: source changed by Bryan Donlan <bdonlan@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.4.0~beta1.hg20070418.227.22a65c23850b-0~pre0
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
scons -c -C src
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Cleaning targets ...
scons: done cleaning targets.
rm -f src/.sconsign.dblite
dh_clean 
 dpkg-source -b zfs-fuse-0.4.0~beta1.hg20070418.227.22a65c23850b
dpkg-source: building zfs-fuse using existing zfs-fuse_0.4.0~beta1.hg20070418.227.22a65c23850b.orig.tar.gz
dpkg-source: building zfs-fuse in zfs-fuse_0.4.0~beta1.hg20070418.227.22a65c23850b-0~pre0.diff.gz
dpkg-source: cannot represent change to src/path.pyc: binary file contents changed
dpkg-source: building zfs-fuse in zfs-fuse_0.4.0~beta1.hg20070418.227.22a65c23850b-0~pre0.dsc
dpkg-source: unrepresentable changes to source

```

---

### Post by shaggy999 on 2007-09-10
I figured out the problem (or at least I figured out a workaround).

Instead of:
```
dpkg-buildpackage -rfakeroot -us -uc
sudo dpkg -i ../zfs-fuse_0.4.0~beta1.hg20070418.227.22a65c23850b-0~pre0_*.deb
```

use

```
cd src
scons
scons install
```

---

### Post by mhacleth on 2007-09-24
Thanks for this workaround. ;-) 
Worked like charm.

---

