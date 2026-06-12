---
title: "[Ubuntu 16.10] can no more launch executable from Nautilus"
date: 2016-10-31
forum: General Help
---

### Post by Le Gluon du Net on 2016-10-31
Hello,

I can no more launch executables from Nautilus if I compiled them myself.
This bug appeared since I upgraded to Ubuntu 16.10.
Precisions:
- I'm talking about executable files, no script files
- the executable I compiled are already executable (chmod +x)

Thank you for your help.

LGDN

---

### Post by Le Gluon du Net on 2016-11-03
up

---

### Post by Le Gluon du Net on 2016-11-17
it seems to be related to PIE and file manager:
[https://bugzilla.gnome.org/show_bug.cgi?id=737849](https://bugzilla.gnome.org/show_bug.cgi?id=737849)
[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1639531](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/1639531)
[https://glandium.org/blog/?p=3310](https://glandium.org/blog/?p=3310)
[https://ubuntuforums.org/showthread.php?t=2341593](https://ubuntuforums.org/showthread.php?t=2341593)
Same bug with Thunar.
Dolphin-emu is the only executable I compiled I can launch from Nautlus  (not see as a shared library), I don't know how they did that.

---

