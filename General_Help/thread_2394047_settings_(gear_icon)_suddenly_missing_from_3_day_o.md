---
title: "settings (gear icon) suddenly missing from 3 day old bionic beaver install"
date: 2018-06-11
forum: General Help
---

### Post by mathum on 2018-06-11
the app launcher does not show it, nor does it show up in a search. How do i get it back?

---

### Post by PaulW2U on 2018-06-12
Hi mathum, first of all we need to establish whether the Settings application is still installed or whether it has inadvertently been removed.

In a terminal, what is the output of
```
apt policy gnome-control-center
```
If you see "(none)" against "Installed" then the application needs to be reinstalled with:
```
sudo apt install gnome-control-center
``` or better still:
```
sudo apt install ubuntu-desktop --reinstall
``` as other applications might also have been removed.

Do you now see the Settings application when searching with the Windows or Super key for either "gnome-control-center" or "Settings" ? Has the application now reappeared on the Ubuntu launcher?

---

### Post by mathum on 2018-06-12
Terrific, that did the trick. I can't imagine why the apps disappeared. New SSD. Maybe it's defective.
Many thanks, PaulW2U

---

