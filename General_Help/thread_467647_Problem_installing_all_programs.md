---
title: "Problem installing all programs"
date: 2007-06-07
forum: General Help
---

### Post by dkowalewski on 2007-06-07
So I installed gcc, but now after running ./cofigure, when I try to run make, it nearly finishes and then says there's a bunch of errors.  Is there any way to fix this?

---

### Post by yabbadabbadont on 2007-06-07
You will have to provide a **lot** more information before anyone will have a prayer of helping you...  :)

---

### Post by dkowalewski on 2007-06-07
sorry... so i'm trying to install QT and when i ran ./configure, everything works fine.  Then when I run the make command, it works fine for the most part, but then this happens.

make[1]: *** [.obj/release-shared/qapplication.o] Error 1
make[1]: Leaving directory `/home/dylan/Desktop/qt-x11-opensource-src-4.3.0/src/gui'
make: *** [sub-gui-make_default-ordered] Error 2

it also says a bunch of files are either 'not included in this scope' or 'argument 1 invalid'

help would be greatly appreciated

---

### Post by yabbadabbadont on 2007-06-07
Two things.  First, you need to post the actual error, where it occurs in the output, not just the summary at the end.  Second, QT is already in the repositories and can easily be installed using Synaptic, Adept, apt-get, or aptitude.  Why are you trying to build it from source?

---

### Post by dkowalewski on 2007-06-07
well, i'm a total noob with linux and didn't know that.... what exactly is the command to install it from synaptec?

---

### Post by yabbadabbadont on 2007-06-08
Just hit the search button in synaptic and type in 'qt' and hit enter.  Then scroll down to the packages that start with "libqt" and select the ones you want.  Normally though, the needed qt libraries will automatically be pulled in whenever you choose to install another program that needs them.  Unless you are trying to do QT development, in which case you will want to install the "libqt" packages that end with "*-dev" as these are the development versions of the libraries.

---

### Post by yabbadabbadont on 2007-06-08
By the way, in gnome you can find synaptic here:

System->Administration->Synaptic Package Manager

---

### Post by dkowalewski on 2007-06-08
thank you so much.

---

