---
title: "X doesn't start"
date: 2006-11-04
forum: General Help
---

### Post by eremini on 2006-11-04
Hello,
A while ago, before final, I updated my friend's computer to edgy from dapper, but since then X doesn't start anymore. When you select yes to view the log, it's just blank, it seems like it doesn't even get to starting X, when you execute X from a command line it starts fine with the normal gray screen. Any ideas?

---

### Post by taurus on 2006-11-04
Probably need to configure X again.  Try booting into recover mode from GRUB and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```
Reboot and see if the GDM login screen appears...

---

