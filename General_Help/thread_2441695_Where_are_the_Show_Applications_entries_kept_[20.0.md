---
title: "Where are the Show Applications entries kept? [20.04]"
date: 2020-04-25
forum: General Help
---

### Post by jebi on 2020-04-25
Hi

In show applications I seem to have acquired an extra software center I have
 
Ubuntu Software and Software the same icon how do I delete one of them?
Seems to have happened after install flatpak.
 
thx

---

### Post by Dennis N on 2020-04-26
**Ubuntu Software** icon should be for a snap version of Gnome Software. It's installed by default.
The **Software** icon should be the apt version of Gnome Software. Check: do you have **gnome-software** installed? It isn't installed when doing a fresh install.
These are similar, except Gnome Software installed by apt has a Flatpak plugin available to manage Flatpaks. It also has a Snap plugin (included by default) to manage Snap packages.

You say you want to delete one of them? You do that by uninstalling the program it represents.

In my install of Ubuntu 20.04, I removed the snap version (the snap package name is '**snap-store**') and installed gnome-software since I wanted the Flatpak support.

---

