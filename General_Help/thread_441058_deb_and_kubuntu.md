---
title: "deb and kubuntu"
date: 2007-05-12
forum: General Help
---

### Post by stevennp on 2007-05-12
Can I get a little help with kubuntu from here? With Ubuntu you can just double click on a deb package and it will install the package and all the dependensies for that package. I tried the same thing in kubuntu and it just loads up ARK. I also right click on the deb and clicked install package but it just comes up with an error because the dependensies were not installed.

---

### Post by strabes on 2007-05-12
You have to use dpkg or install a gui package installer: ```
sudo dpkg -i /path/to/package.deb
```

---

### Post by anjilslaire on 2007-05-12
Or install gdebi, the gnome deb installer (which I prefer even with kubuntu):
sudo apt-get install gdebi


then you can right-click the file, and select Open With Gdebi Package Installer

---

### Post by earobinson on 2007-05-12
> **anjilslaire said:**
> Or install gdebi, the gnome deb installer (which I prefer even with kubuntu):
sudo apt-get install gdebi
that will work, im pretty sure it will also install a lot of garbage, I know kde apps tend to be slower on gnome, so I assume that gnome apps are slower on kde.

---

