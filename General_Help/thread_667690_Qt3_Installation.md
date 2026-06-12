---
title: "Qt3 Installation"
date: 2008-01-14
forum: General Help
---

### Post by jflowers on 2008-01-14
I am trying to install qt3 version  3.3.8 from source code because a program I want to install requires Qt3.  After unpacking the files I run configure and everything appears fine.  When I run make the following error occurs:  

elease-shared/moc_qmotifstyle.o  -L/usr/X11R6/lib -lXext -lX11 -lm -ldl 
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
make[2]: *** [../lib/libqt.so.3.3.8] Error 1
make[2]: Leaving directory `/usr/local/qt/src'
make[1]: *** [sub-src] Error 2
make[1]: Leaving directory `/usr/local/qt'
make: *** [init] Error 2

I can not figure out what is wrong.   I appreciate your help.

---

