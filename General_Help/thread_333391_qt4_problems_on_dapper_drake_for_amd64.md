---
title: "qt4 problems on dapper drake for amd64"
date: 2007-01-07
forum: General Help
---

### Post by kslavin on 2007-01-07
I'm having problems installing qt4 on an AMD64 machine running dapper drake. When running synaptic, I get messages (e.g. for libqt4-core) like: "Depends: libqt4-gui but is not going to be installed" or "Depends: libs-static-pic but is not installable" for all the qt4 libraries except qt4-doc. Is this a known problem - is there a fix? I was trying to install quackle which needs qt4.

---

### Post by disturbedite on 2007-01-27
i was unable to compile quackle.  i wanted to compile it and make a deb for myself and i was gonna post it for you as well, but no such luck...

i'm pretty sure i have all the correct dependencies installed, including all qt4 needed devel packages.  i get a ways into compiling in /quackio/ and then console spits this out:
gcgio.cpp:334: error: ‘letterStringToQString’ is not a member of ‘QuackleIO::Util’
gcgio.cpp: At global scope:
gcgio.cpp:338: error: ‘QString’ does not name a type
make: *** [gcgio.o] Error 1

sorry.  :confused:

---

