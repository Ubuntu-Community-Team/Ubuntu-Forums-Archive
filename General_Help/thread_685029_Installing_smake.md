---
title: "Installing smake"
date: 2008-02-01
forum: General Help
---

### Post by omidomid on 2008-02-01
Hello, I'm trying to install the smake compiler. I downloaded the tar.gz file, extracted using tar -xvzf <filename>, and then typed "make" to compile the program. When I type smake though, it says it's not installed.

Can anyone help a n00b out?

---

### Post by taurus on 2008-02-01
Don't you have to install it first before you use it?

```
sudo make install
```
And if you want to run it without installing it, then you need to be in the same directory of where the smake is.

```
./smake
```

---

### Post by omidomid on 2008-02-01
the ./smake worked, but i guess its still not installed.
When I run sudo make install, here's what happens:

root@OMID-PC:/home/omidomid/Desktop/smake/smake-1.2# sudo make install
NOTICE: Using bootstrap 'Makefile' to make 'install'
cd psmake; sh MAKE
Checking for working bootstrap make...
Smake release 1.2a1 Copyright (C) 1985, 87, 88, 91, 1995-1999 J&#65533;rg Schilling
psmake/smake install
        ==> MAKING "install" ON SUBDIRECTORY "SRCROOT/conf"
install: nothing to make
        ==> MAKING "install" ON SUBDIRECTORY "SRCROOT/inc"
        ==> MAKING "install" ON SUBCOMPONENT "SRCROOT/inc/align_test.mk"
        ==> MAKING "install" ON SUBCOMPONENT "SRCROOT/inc/avoffset.mk"
        ==> MAKING "install" ON SUBDIRECTORY "SRCROOT/lib"
        ==> MAKING "install" ON SUBCOMPONENT "SRCROOT/lib/libschily.mk"
        ==> The folloging messages may occur:
        ==> cannot find include file: <align.h>
        ==> cannot find include file: <avoffset.h>
        ==> this is not an error, these files are made during the build.
        ==> MAKING "install" ON SUBDIRECTORY "SRCROOT/smake"
        ==> MAKING "install" ON SUBCOMPONENT "SRCROOT/smake/Makefile.def"
        ==> MAKING "install" ON SUBCOMPONENT "SRCROOT/smake/Makefile.man"
        ==> MAKING "install" ON SUBDIRECTORY "SRCROOT/man"
        ==> MAKING "install" ON SUBDIRECTORY "SRCROOT/man/man4"
        ==> MAKING "install" ON SUBCOMPONENT "SRCROOT/man/man4/makefiles.mk"
        ==> MAKING "install" ON SUBCOMPONENT "SRCROOT/man/man4/makerules.mk"
root@OMID-PC:/home/omidomid/Desktop/smake/smake-1.2# smake
The program 'smake' is currently not installed.  You can install it by typing:
apt-get install smake
You will have to enable component called 'universe'
bash: smake: command not found
root@OMID-PC:/home/omidomid/Desktop/smake/smake-1.2#     


...what's 'universe?

---

### Post by taurus on 2008-02-01
Looks like smake is in the repos and all you have to do is enable it before you can install it.  Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark in front of all the lines except the last one, Source code, and the Cdrom in the window below.  Close it.  Then, press Refresh and in the Search field of synaptic, type smake to search for it and install it there.

---

### Post by omidomid on 2008-02-01
Can't seem to find "System -> Administration -> Synaptic Package Manager -> Settings -> Repositories". I'm running Kubuntu if that has anything to do with it..?

---

### Post by taurus on 2008-02-01
Yes.  

Not sure where synaptic is in KDE but open a terminal and run

```
kdesu synaptic
```

---

### Post by omidomid on 2008-02-06
This is what I get:

root@OMID-PC:/home/omidomid# kdesu synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdesu: cannot connect to X server :0.0
root@OMID-PC:/home/omidomid#

---

