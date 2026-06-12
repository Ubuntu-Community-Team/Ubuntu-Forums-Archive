---
title: "Source packages PROBLEM"
date: 2007-05-03
forum: General Help
---

### Post by mikedragon on 2007-05-03
Hi! I always have problems when I try to install source packages (tar.gz or tar.bz2) on both Ubuntu & and Kubuntu. I've decided to ask you, so the example can be Domino 0.4. Some screenshots:

[IMG]http://img149.imageshack.us/img149/4830/zrzutekranudomino0pngup7.jpg[/IMG]
this is directory with domino's source files

[[IMG]http://img225.imageshack.us/img225/4333/zrzutekranumisu8.th.jpg[/IMG]](http://img225.imageshack.us/my.php?image=zrzutekranumisu8.jpg) 
I tried to install it. Dunno why, I couldn't. When I wrote 'make' it complains about not found object 'makefile' and when I wrote 'sudo make install' it complains about no rules to make install. The next thing is that I have troubles with EVERY source package which I want to install. If someone knows what's going on, so please tell me.

Thanks,
mikedragon

---

### Post by gerscht on 2007-05-03
Might be to obvious, but do you have your build-essentials installed?

---

### Post by mikedragon on 2007-05-03
No, and i'm installing it now. I'll tell you if it works

---

### Post by mikedragon on 2007-05-03
It complains now about no X libraries on ./configure... Make'n'sudo make install still don't work

---

### Post by thelocust on 2007-06-08
You need to install xlibs-dev and then it will probably give you some other errors. Mine says:
```
checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!
```

---

