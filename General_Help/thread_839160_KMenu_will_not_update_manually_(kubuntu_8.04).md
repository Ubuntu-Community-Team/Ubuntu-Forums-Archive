---
title: "KMenu will not update manually (kubuntu 8.04)"
date: 2008-06-24
forum: General Help
---

### Post by eyal p on 2008-06-24
Hello,I have this annoying problem: I cannot change K Menu manually. I can edit it allright, save it, but when I open the menu nothing is changed - no matter what I do.
I can not find which file is the relevant one and what is its path.
KDE Menu Editor version 0.7.
KDE 3.5.9.
Ideas anybody?
:confused:

---

### Post by Zorael on 2008-06-24
Curious. Try doing the following in a terminal.
```
$ sudo chown `whoami` ~/.config/menus -R
$ kbuildsycoca
```

---

### Post by eyal p on 2008-06-25
This is what I got:

eyal@eyal-laptop:/$ sudo chown `whoami` ~/.config/menus -R
eyal@eyal-laptop:/$ kbuildsycoca
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: WARNING: Parse error in /home/eyal/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/eyal/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file

---

