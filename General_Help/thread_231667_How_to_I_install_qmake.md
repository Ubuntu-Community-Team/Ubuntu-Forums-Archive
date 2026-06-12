---
title: "How to I install qmake?"
date: 2006-08-07
forum: General Help
---

### Post by lechium on 2006-08-07
Hi,

I've been trying to install last.fm player, and it requires qmake (and qt4 tools) in order to compile it properly.
I had downloaded dq4 development tools and such, but qmake was nowehere to be found. I did some searhces and there seems to be no qmake for Dapper... is it true or I missed something?

thanks,
Victor

---

### Post by lechium on 2006-08-07
*bump*

---

### Post by mlind on 2006-08-07
```

sudo aptitude install qt3-dev-tools

```

(or libqt4-dev)

---

### Post by lechium on 2006-08-07
Still no qmake...

---

### Post by mlind on 2006-08-08
libqt4-dev provides /usr/bin/qmake-qt4, isn't that what you're looking for?

---

### Post by Sir_Sid on 2006-09-03
Im trying to install the same thing and Im following the readme which says this :

uild instructions
==================

Before starting the compilation process, make sure you're really
using the Qt4 toolchain. Running "qmake -v" should identify as
version 4.x.x.

To compile the Last.fm Client, follow these steps:

$ qmake
$ make


Starting the Last.fm Client
===========================

$ ./lastfm



now I do what it says but when i type in make nothing happens.

---

### Post by mlind on 2006-09-03
Did you install **build-essential** package?

---

### Post by Blario on 2006-10-07
Yooo, I'm on this too.  I tried compiling qt4 from source from trolltech(sp?).com, and that froze my comp everytime I did, therefore I went looking for some built i386 ubuntu and/or debian packages.

I just finally got qt4-dev-tools_4.0.0-3ubuntu1_i386.deb to install by meeting requirements.  More recent version of the pack require too many unstable libraries that ubuntu hasn't even put out.  Alass, Same issue, when I run "qmake -v" I still get "Qmake version: 1.07a (Qt 3.3.6)" from when I installed Qt3.

Qt3.3.6 doesn't seem to be new enough, becuase by following the ReadMe from above, running "qmake" in the Last.fm directory doesn't do anything.  The ReadMe does say that Qt4 is required, but qt4-dev-tools didn't change the version # of my qmake... basically I think I need to find out what package qmake is included in.  Thanks..

---

### Post by Jamhos on 2006-10-26
I have the same problem as Blario - it says I have "Qmake version: 1.07a (Qt 3.3.6)". Also, I have installed Qt4 Designer, but can't get it to run, and can't find it anywhere. *shrugs*

---

### Post by ookami on 2006-11-02
First make sure you remove the "libqt3-devtools" package then (re)install "libqt4-dev-tools". It did the trick for me.

---

### Post by Blario on 2006-11-03
Alright.  New problem.  Qt wouldn't compile from source on my desktop, which I'm pretty sure it's an overheating problem (computer keeps locking up)... So I compiled it on my laptop just now.  It took probably some time more than half an hour, but it did it!

So I have Qt installed now no problem, AND it's the most current stable working version.

[email]root@ubuntu:/opt/Last.fm[/email]_Client_1.0.0b# qmake -v
QMake version 2.01a
Using Qt version 4.2.1 in /usr/local/Trolltech/Qt-4.2.1/lib

Awesome!  Tell me why, when I run "qmake" in the Last.fm source directory, following the Last.fm README instructions, still nothing happens.  All I get is the qmake help message print-out, describing how to use the command.  I know at this point that I have all the right Qt software installed, I believe that the README just has the wrong command written in it.  What is the right qmake command that should be run in the Last.fm source directory?

---

### Post by arrizaba on 2006-11-15
To run lastfm you don't need to compile it. Just run ./lastfm
I don't know why the README says you should compile it....it's very confusing, indeed.

---

### Post by Blario on 2006-11-15
That's quite amazing.  I'm so accustomed to assuiming the documentation that comes with open source software is accurate and to the point.  It didn't occur to me that Qt is an environment and that Last.fm didn't have to be compiled to run it.  Quite amazing!

THANKS for the help from everyone that helped me.  This really is a favorite app of mine and I'm glad that I have it back.

---

