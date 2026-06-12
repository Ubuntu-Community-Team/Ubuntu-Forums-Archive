---
title: "aptitude recommends help"
date: 2007-10-15
forum: General Help
---

### Post by maybeway36 on 2007-10-15
Is there a way to use a one-line command to install Firefox and not ubufox with Aptitude?
Ubufox is recommended by Firefox.
I could use the --without-recommends option, but I am going to install other applications in the same line and want to install the recommends for those.

---

### Post by Pumalite on 2007-10-15
Download tar.gz from firefox site to your Desktop, then at the Terminal:
cd ~/Desktop
tar xvzf firefox-2.0.0.7.tar.gz
cd firefox
./firefox

---

### Post by maybeway36 on 2007-10-15
I'd rather use APT, to avoid duplicating dependencies, and so automatic upgrades go through APT.
I'll tell my shell script to install Firefox, then uninstall ubufox, and see how that works.

---

