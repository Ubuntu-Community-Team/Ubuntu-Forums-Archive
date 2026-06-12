---
title: "After crash startmenu disappeared"
date: 2007-09-14
forum: General Help
---

### Post by Darkeagle on 2007-09-14
My startmenu is disappeared. Above Places and System there are usually the applications:

[http://img401.imageshack.us/img401/9448/screenshotmc3.png](http://img401.imageshack.us/img401/9448/screenshotmc3.png)

The problems start after the whole ubuntu-partition was full. Now I have more space on this partition, but I can't go to my applications and I can't start the alacarte menu-editor. Maybe an executable or a configfile of the gnomemenu is damaged. However all applications are still in the directory /usr/share/applications.

---

### Post by jamvegan on 2007-09-14
You might try:
```
sudo apt-get -f install
```
to try to fix any broken packages.  Perhaps also:
```
sudo apt-get --reinstall install ubuntu-desktop
```
(or xubuntu-desktop, edubuntu-desktop, etc., as appropriate) to make sure all of the standard desktop packages are still installed.

---

