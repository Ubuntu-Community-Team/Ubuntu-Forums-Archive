---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2007-03-03
forum: General Help
---

### Post by olskar on 2007-03-03
I get this error when I have use "sudo apt-get autoremove"

> askar@barbara:~$ sudo apt-get autoremove 
Läser paketlistor... Färdig
Bygger beroendeträd         
Reading state information... Färdig
0 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
1 ej helt installerade eller borttagna.
Behöver hämta 0B arkiv.
Efter uppackning kommer 0B ytterligare diskutrymme användas.
Ställer in python-mutagen (1.7.1-0ubuntu1) ...
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/mutagen/_constants.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/mutagen/_constants.py
dpkg: fel vid hantering av python-mutagen (--configure):
 underprocess post-installation script gav felkod 1
Fel uppstod vid hantering:
 python-mutagen
E: Sub-process /usr/bin/dpkg returned an error code (1)

How do I solve that?

---

### Post by olskar on 2007-03-03
solved it!
removed /usr/lib/python2.4/site-packages/mutagen/ and reinstalled mutagen

---

