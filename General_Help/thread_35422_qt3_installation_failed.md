---
title: "qt3 installation failed"
date: 2005-05-18
forum: General Help
---

### Post by kozmo on 2005-05-18
I downloaded qt-x11-free-3.3.4 from trolltech.com and followed the instructions in the install file. Everything goes fine until the MAKE command. I get the following errors:

[HTML]ns_x11.o kernel/qtaddons_x11.cpp
In file included from kernel/qtaddons_x11.cpp:25:
kernel/qt_x11_p.h:66:22: X11/Xlib.h: No such file or directory
kernel/qt_x11_p.h:71:23: X11/Xutil.h: No such file or directory
kernel/qt_x11_p.h:72:21: X11/Xos.h: No such file or directory
kernel/qt_x11_p.h:73:23: X11/Xatom.h: No such file or directory
make[2]: *** [.obj/release-shared-mt/qtaddons_x11.o] Error 1
make[2]: Leaving directory `/opt/qt/src'
make[1]: *** [sub-src] Error 2
make[1]: Leaving directory `/opt/qt'
make: *** [init] Error 2
root@lisa:/opt/qt#
[/HTML]

Has anyone gotten qt3 to install on Hoary?

---

### Post by dave9191 on 2005-05-19
Looks like you are missing some X11 headers. You need to install them ( i forgot the package name ), but browse sytaptic and find stuff with X11 and -dev and intsal that. What did configure say when you run that ? 

Dave

---

### Post by kozmo on 2005-05-19
configure ran fine -- no errors at all.

I'll install the X11 headers tonight after work -- thanks!

[QUOTE=dave9191]Looks like you are missing some X11 headers. You need to install them ( i forgot the package name ), but browse sytaptic and find stuff with X11 and -dev and intsal that. What did configure say when you run that ? 

Dave[/QUOTE]

---

### Post by dave9191 on 2005-05-19
i would have expecetd configure to complain about not seeing the x header files. Tell me how it goes. 

Dave

---

### Post by kozmo on 2005-05-20
I installed libx11-dev package, synapitc automaticaly selected a dozen or so other packages to installed.

I ran configue and make, and after several hours Qt was installed and ready to go.

Thanks!

---

### Post by dave9191 on 2005-05-20
Good to hear :) 

Dave

---

