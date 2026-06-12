---
title: "Init Command"
date: 2004-11-18
forum: General Help
---

### Post by Tarisutan on 2004-11-18
I type init 3 and nothing really happens it is supposed to kill all processes but nothing really happens it looks like it may be working but then when I try to install the nvidia driver it says that x server is still running...How can I fix this?

---

### Post by FLeiXiuS on 2004-11-18
[QUOTE=Tarisutan]I type init 3 and nothing really happens it is supposed to kill all processes but nothing really happens it looks like it may be working but then when I try to install the nvidia driver it says that x server is still running...How can I fix this?[/QUOTE]


The command, init 3 is irrelevant in debian.   Debian's runlevel's 2-5 are all multi-user/gdm levels.  Fail safe terminal can be found at runlevel1.  Which might be what your looking for. 

I also prefer using telinit instead of just init.  Don't ask why.
```
sudo telinit 1
```

Init 1 is a single-user mode. 

Debian Runlevels
0 - shut down the system
1 - single-user mode
2 - 5 multi-user mode
6 - reboot

NOTE: Debian's runlevels are much different then Redhat/Fedora's runlevels.  This seems to be where you have came from.  

For more info, [http://qref.sourceforge.net/Debian/reference/ch-system.en.html#s-custombootscripts](http://qref.sourceforge.net/Debian/reference/ch-system.en.html#s-custombootscripts)

---

