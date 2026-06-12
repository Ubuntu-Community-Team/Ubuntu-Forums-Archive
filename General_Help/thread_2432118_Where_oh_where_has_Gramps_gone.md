---
title: "Where oh where has Gramps gone"
date: 2019-11-27
forum: General Help
---

### Post by harfin on 2019-11-27
Can anyone give me a simple "How To" guide to installing the **Gramps** software that is **not **available via Ubuntu Software?

---

### Post by Holger_Gehrke on 2019-11-27
Is [this]("https://gramps-project.org") the Gramps you're talking about ? Then I can tell you that it actually is in the repositories but Ubuntu Software doesn't show it, probably because of missing appstream metadata. A simple 'sudo apt install gramps' in a terminal will download and install the program. Depending on the release of Ubuntu you're running this might install a rather old version (see [Ubuntu Package Search]("https://packages.ubuntu.com/search?keywords=gramps&searchon=names")). If you need (or want) the current version, the instructions at [gramps-project.org]("https://www.gramps-project.org/wiki/index.php/Download#Linux:_Install_latest_version") look simple enough ...

Holger

---

### Post by Dennis N on 2019-11-27
It's in the Ubuntu repository. You can install with a terminal command:
```
sudo apt install gramps
```

---

### Post by HermanAB on 2019-11-27
[https://gramps-project.org/wiki/index.php/Download#Linux:_Install_latest_version](https://gramps-project.org/wiki/index.php/Download#Linux:_Install_latest_version)

---

### Post by Buntu Bunny on 2019-11-27
You can also install it via Synaptic Package Manager. It's listed there.

---

### Post by harfin on 2019-11-28
Grateful thanks to all!
Alan

---

