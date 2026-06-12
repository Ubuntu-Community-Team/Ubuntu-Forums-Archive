---
title: "help install ati drivers"
date: 2006-12-24
forum: General Help
---

### Post by cptjaben on 2006-12-24
I'm following [this]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installation") guide to install ati drivers for my radeon 9700. Under section 1.1 it says, "Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!" How do I enable this repository? Thanks much.

---

### Post by taurus on 2006-12-24
By removing the # in front of all the lines with universe & multiverse (usually start with **deb**) in /etc/apt/sources.list...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

