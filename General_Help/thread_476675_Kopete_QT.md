---
title: "Kopete QT"
date: 2007-06-17
forum: General Help
---

### Post by sprinkles on 2007-06-17
I have Kopete installed and running fine (installed with aptitude). There is a bug meaning that the webcam does not work, however.
There is a patch for this, but to install it you have to patch a file and compile it. I've applied the patch to the required file, but Kopete won't compile because it can't find Qt. I know it must be installed because it runs fine, and "whereis qt3" gives 3 locations, but I can't get it to compile.

I've tried ./configure --with-qt-dir=/etc/qt3, ./configure --with-qt-dir=/usr/lib/qt3
, and ./configure --with-qt-dir=/usr/share/qt3, but it still says:

checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!


Does anyone know how i can get it compiled?

---

