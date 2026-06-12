---
title: "LimeWire white screen problem solution."
date: 2008-01-24
forum: General Help
---

### Post by bgoody on 2008-01-24
If you are trying to start Limewire (and apparnetly other Java programs) and get a white screen but nothing else the solution is to install Java 6

sudo apt-get install sun-java6-jdk #sun-java6-plugin

When it is finsihed installing you have to get Ubuntu to use that version rather than an older one.

 sudo update-alternatives --config java

Choose Sun Java 6.  You should be good to go now.

---

### Post by jesushero on 2008-01-25
LimeWire uses java?

---

