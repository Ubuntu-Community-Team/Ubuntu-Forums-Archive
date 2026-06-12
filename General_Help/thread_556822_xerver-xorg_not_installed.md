---
title: "xerver-xorg not installed?"
date: 2007-09-21
forum: General Help
---

### Post by jonaaathan on 2007-09-21
When I try to reset my xserver.xorg i get this:

$ sudo dpkg-reconfigure xserver.xorg
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed


I already tried doing
```
sudo apt-get install ubuntu-desktop
```
and
```
sudo apt-get install xserver-xorg
```

but it just told me that I already have the installed and have the latest files.  Please help! I'm a Linux noob :(


edit:
ah found out that ```
dpkg-reconfigure xserver-xorg
``` fixed it.

---

### Post by PmDematagoda on 2007-09-21
Glad to see you solved your problem, could you mark this thread as solved as it could help other users who may be having the same problem as you did?:)

---

