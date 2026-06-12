---
title: "Uninstall app by source code ?"
date: 2007-07-09
forum: General Help
---

### Post by mocqueanh on 2007-07-09
I knew 2 ways to uninstall app in Ubuntu:
apt-get or aptitude to remove app and its dependcies
dpkg -r to remove only app (and leave its dependcies)


And when read the file INSTALL in source code package, except of ./configure to install, it says:

make clean to remove.

I dont know this command is use to uninstall app or only delete source code ? :guitar:

---

### Post by HermanAB on 2007-07-09
'make clean' usually just prepares the system for a fresh compile cycle.

Try 'make uninstall' to remove a package.

---

### Post by mocqueanh on 2007-07-11
make uninstall remove only app, not remove dependcies ?

---

### Post by hooksie on 2007-07-11
(Not on my Ubuntu install right now, so I cant test this, but...)

Isn't it something like

sudo apt-get autoremove

to remove dependencies that are no longer needed?  Confirm anyone?

---

