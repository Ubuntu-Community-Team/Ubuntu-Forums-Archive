---
title: "qt4's Opengl library"
date: 2008-05-12
forum: General Help
---

### Post by themostunoriginalname on 2008-05-12
Tried this:

$sudo apt-get install libqt4-opengl-dev libqt4-devReading package lists... Done
Building dependency tree
Reading state information... Done
libqt4-dev is already the newest version.
The following NEW packages will be installed:
  libqt4-opengl-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/39.0kB of archives.
After this operation, 233kB of additional disk space will be used.
(Reading database ... 178255 files and directories currently installed.)
Unpacking libqt4-opengl-dev (from .../libqt4-opengl-dev_4.4.0-1ubuntu3~hardy1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu3~hardy1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/pkgconfig/QtOpenGL.pc', which is also in package libqt4-dev
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu3~hardy1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Then, tried this:
$ sudo dpkg --force-overwrite -i /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu1~hardy1_i386.deb
dpkg: error processing /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu1~hardy1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu1~hardy1_i386.deb

Any ideas?

---

### Post by m95lag on 2008-05-12
Having exactly the same problem. The libqt4-opengl-dev_4.4.0-1ubuntu3~hardy1_i386.deb package won't install. Would also be grateful for some help.

---

### Post by aos101 on 2008-05-12
Apparently it's a bug in the packaging:

[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/228148](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/228148)

The bug has a few comments about how you might be able to force the install of the package.

---

### Post by themostunoriginalname on 2008-05-13
yea... I looked at that before posting here and what I showed up there was stuff that I tried from that post.

---

### Post by m95lag on 2008-05-13
Using the force-all instead of force-owerwrite switch to dpkg as described in that bug-thread worked for me.
I.e: sudo dpkg --force-all -i /var/cache/apt/archives/libqt4-opengl-dev_4.4.0-1ubuntu3~hardy1_i386.deb

Gave a warning, but the libs seem to have been installed.
Cheers aos101.

> **aos101 said:**
> Apparently it's a bug in the packaging:

[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/228148](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/228148)

The bug has a few comments about how you might be able to force the install of the package.

---

### Post by themostunoriginalname on 2008-05-13
Thanks. It worked.

---

### Post by barmaley on 2008-05-23
Thank you, it worked for me too.
I needed this for Qtiplot installation from sources.

---

