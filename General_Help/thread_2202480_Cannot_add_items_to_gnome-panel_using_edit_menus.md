---
title: "Cannot add items to gnome-panel using edit menus"
date: 2014-01-29
forum: General Help
---

### Post by defaria on 2014-01-29
Ubuntu 13.10 but I'm still using the Gnome classic environment with gnome-panel. When I try to use Edit Menus to add an item it fails. What I've learned is that Edit Menus is really alacarte. And that it stores data under ~/.local/share/applications. When I attempt to make a new item I get a file made called alacare-made.desktop that contains:

```
[Desktop Entry]
Comment=
Terminal=false
Name=Software Updater (DeFaria.com)
Exec=ssh defaria.com sudo /usr/sbin/update-manager
Type=Application
Icon=gnome-panel-launcher

```

I was attempting to add an entry that would ssh from my desktop machine and execute update-manager on another machine in my LAN. This, however, never appears in the menu. If I instead copy the update-manager.desktop file to say update-defaria.com.desktop and then edit it by hand viola! I get my entry in the menu.

Why is this broken and how can I fix it?

---

