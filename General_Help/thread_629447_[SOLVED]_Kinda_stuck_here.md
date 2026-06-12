---
title: "[SOLVED] Kinda stuck here"
date: 2007-12-02
forum: General Help
---

### Post by TidusBlade on 2007-12-02
I have a fresh install of Ubuntu Dapper Drake, and I am trying to install the latest package of rtorrent and it returns this:
```
root@89-149-240-61:~# dpkg -i rtorrent_0.7.4-2ubuntu2_i386.deb
Selecting previously deselected package rtorrent.
(Reading database ... 13622 files and directories currently installed.)
Unpacking rtorrent (from rtorrent_0.7.4-2ubuntu2_i386.deb) ...
dpkg: dependency problems prevent configuration of rtorrent:
 rtorrent depends on libc6 (>= 2.6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 rtorrent depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not installed.
 rtorrent depends on libgcc1 (>= 1:4.2-20070516); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 rtorrent depends on libidn11 (>= 0.5.18); however:
  Package libidn11 is not installed.
 rtorrent depends on libkrb53 (>= 1.6.dfsg.1); however:
  Version of libkrb53 on system is 1.4.3-5ubuntu0.1.
 rtorrent depends on libssl0.9.8 (>= 0.9.8e-1); however:
  Version of libssl0.9.8 on system is 0.9.8a-7build1.
 rtorrent depends on libstdc++6 (>= 4.2-20070516); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 rtorrent depends on libtorrent10; however:
  Package libtorrent10 is not installed.
dpkg: error processing rtorrent (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rtorrent

```
I am assuming that I need to upgrade dependencies, which is kind of a problem for me, since the new dependencies are in the gutsy repos and I am using dapper repos, so does anyone know how can I safely upgrade those dependencies and then install "rtorrent".
Any help appreciated :D

---

### Post by p_quarles on 2007-12-02
It looks like some of those packages (such as libcurl3) are simply not installed at all. Before anything else, try getting all the dependencies for rtorrent:
```
sudo apt-get build-dep rtorrent
```
If that doesn't help, then you're probably right about the right packages not being available in Dapper. You can, of course, get .debs for all those dependencies via the web from packages.ubuntu.com .

Of course, this will be a bit of a pain, and it may turn out that those dependencies have further dependencies, and so forth.

---

### Post by TidusBlade on 2007-12-02
Thanks, im starting the painful journey to gather all dependencies :P

---

