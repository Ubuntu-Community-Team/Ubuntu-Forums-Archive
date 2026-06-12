---
title: "[SOLVED] Installing MuseScore 0.6.1 in Ubuntu 7.04"
date: 2007-08-20
forum: General Help
---

### Post by gmjs on 2007-08-20
Hi,

I downloaded a copy of MuseScore (music notation software) version 0.5 and successfully compiled it with Qt 4.2.  A newer version has since been released and I would like to upgrade.

Version 0.6.1 of MuseScore requires Qt 4.3 or above, so I downloaded and installed Qt 4.3.1.

I've followed the installation instructions and added the Qt directory (/usr/local/Trolltech/Qt-4.3.1) to the PATH variable and CMake (which is required to compile MuseScore) reports this new version as present.

The compilation appears successful, but MuseScore will not run.  The following error appears after the splash screen closes:

**./mscore: symbol lookup error: ./mscore: undefined symbol: _ZN9QListData7detach2Ev**

I've read around and the opinion seems to be that the software compiles with Qt 4.3.1 but then runs with Qt 4.2.  I don't know how to go about changing this.

As an aside, when I compile LyX 1.5.1 without specifying the new Qt directory, it registers Qt 4.2 after running ./configure.  Does anyone know where LyX gets the default version of Qt from?  If so, this might help get MuseScore to run!

All help is greatly appreciated.

Many thanks,

Graham

---

### Post by gmjs on 2007-09-15
Does anyone have any thoughts?

I've just downloaded and compiled the latest version of mscore (0.7.0.1) and get exactly the same error when trying to run the application.

I've got the latest version of Qt and CMake, so I'm really stuck.

Any help greatly appreciated.

Many thanks,

Graham

---

### Post by wschweer on 2007-09-16
on the command line:

export LD_LIBRARY_PATH=/usr/local/Trolltech/Qt-4.3.1/lib:$LD_LIBRARY_PATH
mscore

should do the trick and mscore finds the right libraries.

---

### Post by gmjs on 2007-09-17
Wow! A reply from the guy himself!  Thanks so much - it works now!

Keep up the excellent work! 

Graham

---

