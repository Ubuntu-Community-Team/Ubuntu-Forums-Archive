---
title: "nvidia-settings"
date: 2005-03-27
forum: General Help
---

### Post by Rotarychainsaw on 2005-03-27
It seems that my settings dont take effect until I start this program once, then they stay until I logout. Did I forget to do something to make my settings auto-load at startup?

---

### Post by mark on 2005-03-27
[QUOTE=Rotarychainsaw]It seems that my settings dont take effect until I start this program once, then they stay until I logout. Did I forget to do something to make my settings auto-load at startup?[/QUOTE]
The *nvidia-settings* utility should create a file called *.nvidia-settings-rc* in your home directory.  Make sure it's there - otherwise, you might check your *xorg.conf* file in the */etc/X11* directory.

---

