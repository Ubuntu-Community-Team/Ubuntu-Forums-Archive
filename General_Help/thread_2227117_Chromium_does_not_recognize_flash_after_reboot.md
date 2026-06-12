---
title: "Chromium does not recognize flash after reboot"
date: 2014-05-30
forum: General Help
---

### Post by nonkreon on 2014-05-30
Hello,
I decided to get back to chromium from firefox. I've heard about the flash issue, so I installed the pepperflashplugin-nonfree and set it up. At first, chrome://flash displays pepperflash is installed and working and flash works. After I reboot my computer, flash is no longer recognized until I perform **sudo update-pepperflashplugin-nonfree --install, **chrome://flash shows it is not installed and it is not usable in the browser. Have any idea why this occurs?

Thank you for your time!

---

### Post by bapoumba on 2014-05-31
```
ls -la /usr/lib/flashplugin-installer/
total 17044
drwxr-xr-x   2 root root     4096 mai   16 18:10 .
drwxr-xr-x 122 root root    20480 mai   27 19:46 ..
-rwxr-xr-x   1 root root      791 mai   13 15:41 install_plugin
-rw-r--r--   1 root root 17422820 mai   16 18:10 libflashplayer.so

```
After installing the flash plugin, do you have these files ?

---

### Post by nonkreon on 2014-06-15
Solved the issue, found out that /etc/chromium-browser/default was overwritten by some script with another file in /usr/share, changed the source in there and voila, works like a charm.
Thank you bapoumba, will mark this as solved.

---

