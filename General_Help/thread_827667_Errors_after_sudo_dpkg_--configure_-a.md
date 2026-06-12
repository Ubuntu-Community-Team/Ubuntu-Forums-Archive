---
title: "Errors after sudo dpkg --configure -a"
date: 2008-06-13
forum: General Help
---

### Post by ByRillYAN on 2008-06-13
I had the same error message and tried the same method to fix it and got this message:

> dpkg: error processing gnome-desktop-data (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of gnome-about:
 gnome-about depends on gnome-desktop-data (= 1:2.22.2-0ubuntu2); however:
  Version of gnome-desktop-data on system is 1:2.22.2-0ubuntu1.
dpkg: error processing gnome-about (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-desktop-data
 gnome-about


HELP!

---

### Post by aysiu on 2008-06-13
Can you post the output of these commands? ```
cat /etc/apt/sources.list
sudo apt-get update
```

---

