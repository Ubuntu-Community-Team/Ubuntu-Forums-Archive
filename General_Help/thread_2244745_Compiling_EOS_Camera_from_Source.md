---
title: "Compiling EOS Camera from Source"
date: 2014-09-18
forum: General Help
---

### Post by mastercosgrove on 2014-09-18
This is my second attempt of trying to compile something from source, but just like last time ([http://ubuntuforums.org/showthread.php?t=2241867](http://ubuntuforums.org/showthread.php?t=2241867)) I've had no success.

I tried opening in via command line but to no avail: 

[IMG]http://i.imgur.com/kfPVHmy.png[/IMG]

In the end I just right clicked on the package in the file finder with the GUI:

[IMG]http://i.imgur.com/6mUjeP0.png[/IMG]

Changing the directory and looking at what's inside:

[IMG]http://i.imgur.com/Ogr1mzC.png[/IMG]

There is no READ-ME, INSTALL or configure file. So I am lost what I am supposed to do here.

That config.h.cmake file is really tempting but I don't know if I an excute it and I don't know how I can.

[IMG]http://i.imgur.com/OLmqtkK.png[/IMG]

Thank you for any assistance you can provide.

---

### Post by mastercosgrove on 2014-09-18
I've actually made some progress:

[IMG]http://i.imgur.com/iq1lJzr.png[/IMG]
The problem now is what is causing this problem and how do I fix it?

---

### Post by Impavidus on 2014-09-18
Look again, there is a file named INSTALL in that directory.

Edit: As to tar not unpacking the archive, the z option tells tar to expect gz compression. The file however uses bz2 compression, so you'd have to replace the z with j. Or drop it altogether, as I believe tar is smart enough to figure out the used compression method itself.

---

### Post by mastercosgrove on 2014-09-21
Yeah I figured that out, unforuntely I just get an error everytime trying to install something to compile.

---

### Post by tgalati4 on 2014-09-21
Perhaps you could share the contents of CMakeOutput.log?  It's tough to read from here.

90% of the work is getting a correct build environment for the software that you are trying to compile.  You are trying to duplicate the same tools that were used to develop the software originally.  This takes some effort.  It's also an iterative process.  Once you fix one error, another is sure to pop up.  Patience is key.  Everything is fixable.

---

### Post by steeldriver on 2014-09-21
... for starters, you don't appear to have the pre-requisite Qt4 build environment installed

BTW can you please post text (ideally between [CODE] tags) rather than images? you should be able to copy-paste from the terminal into your browser

---

### Post by tgalati4 on 2014-09-21
To further along your build environment:

> tgalati4@Mint14-Extensa /etc $ apt-cache search qmake
qt4-qmake - Qt 4 qmake Makefile generator tool
qconf - Nice configure script for your qmake-based project

```
sudo apt-get install qt4-qmake qconf build-essential
``` (Notice how I sneaked in the build environment essentials.)

You may need to install some other qt4 stuff:

> qt4-bin-dbg - Qt 4 binaries debugging symbols
qt4-demos - Qt 4 examples and demos
qt4-demos-dbg - Qt 4 examples and demos debugging symbols
qt4-designer - graphical designer for Qt 4 applications
qt4-dev-tools - Qt 4 development tools
qt4-doc - Qt 4 API documentation
qt4-linguist-tools - Qt 4 Linguist tools
qt4-qmake - Qt 4 qmake Makefile generator tool


The general dependencies are usually listed in the INSTALL or README file and the *make/qmake* script will throw errors when specific dependencies are missing or don't match.

---

