---
title: "Getting Minimize / Maximize / Close Buttons on Right Side"
date: 2015-08-12
forum: General Help
---

### Post by paul-james on 2015-08-12
Hi,
I was looking for a way to get the min/max/close buttons on windows to be on the RIGHT SIDE instead of default left side. Currently have ubuntu 14.04.3 x64 installed. 

This fix assumes one is using gnome-fallback (metacity)

If you don't have dconf-editor installed, install it. ```
sudo apt-get install dconf-editor
```.

In dconf-editor go to Org -> Gnome -> Desktop -> WM -> Preferences

Edit the field **button-layout** and it must be set to  ```
menu:minimize,maximize,close
```

Enjoy.

---

