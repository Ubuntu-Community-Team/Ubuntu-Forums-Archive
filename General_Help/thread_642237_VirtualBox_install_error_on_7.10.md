---
title: "VirtualBox install error on 7.10"
date: 2007-12-16
forum: General Help
---

### Post by westsyde on 2007-12-16
Hello, I am a new user of Ubuntu, using 7.10, and I am getting the following error:

me@laptop:~/Desktop$ sudo dpkg -i virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb
Selecting previously deselected package virtualbox.
(Reading database ... 88004 files and directories currently installed.)
Unpacking virtualbox (from virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb) ...
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.5-0ubuntu14.
 virtualbox depends on libgcc1 (>= 1:4.2.1); however:
  Version of libgcc1 on system is 1:4.1.2-0ubuntu4.
 virtualbox depends on libglib2.0-0 (>= 2.14.0); however:
  Version of libglib2.0-0 on system is 2.12.11-0ubuntu1.
 virtualbox depends on libqt3-mt (>= 3:3.3.8really3.3.7); however:
  Package libqt3-mt is not installed.
 virtualbox depends on libssl0.9.8 (>= 0.9.8e-1); however:
  Version of libssl0.9.8 on system is 0.9.8c-4build1.
 virtualbox depends on libstdc++6 (>= 4.2.1); however:
  Version of libstdc++6 on system is 4.1.2-0ubuntu4.
 virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.
 virtualbox depends on zlib1g (>= 1:1.2.3.3.dfsg-1); however:
  Version of zlib1g on system is 1:1.2.3-13ubuntu4.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox

---

### Post by TidusBlade on 2007-12-16
Seem you dont have the right version of the dependencies, all of the listed ones are lower version than required.
```
virtualbox depends on libc6 (>= 2.6-1); however:
Version of libc6 on system is 2.5-0ubuntu14.
```
That means that VB needs libc6 2.6.1 however you have 2.5.0

**The only way I know around this is gathering the dependencies yourself and installing them all, it could be very painful process so good luck ;)**
EDIT: Or you can try installing from "Add/Remove programs" if you havent already, I beilieve it installs all dependencies for you. And [here's](http://packages.ubuntu.com/gutsy/misc/virtualbox-ose) the dependencies page for virtualbox xD

---

### Post by p_quarles on 2007-12-16
westsyde: That is strange. It looks to me like you have many packages which belong to Ubuntu 7.04. Let's make sure that you have the version you think you have:
```
cat /etc/issue
```
The output *should* say Ubuntu 7.10. If it doesn't, something weird is going on.

---

### Post by westsyde on 2007-12-28
DOH!


thank you for the help, I downloaded what was the latest version a couple months ago and never checked the version when installing virtualbox. 

Mahalo very much for saving me the trouble of trying to manually update libraries. VB works like a charm.

---

