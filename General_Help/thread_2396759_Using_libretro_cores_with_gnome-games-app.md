---
title: "Using libretro cores with gnome-games-app?"
date: 2018-07-20
forum: General Help
---

### Post by amano on 2018-07-20
Does anybody know how to use libretro cores with the gnome-games-app?

I installed libretro-nestopia but gnome-games doesn't pick it up. NES Roms are not launched at all.

The official flatpak version works though. That ships the proper libretro core by itself. But having 300 megs installed to launch NES games seems a little excessive...

---

### Post by amano on 2018-07-22
&#504;obody has that working? Maybe a bug?

---

### Post by amano on 2018-07-30
ok. It is a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-games-app/+bug/1682863](https://bugs.launchpad.net/ubuntu/+source/gnome-games-app/+bug/1682863)

Most of the Debian and Ubuntu packages lack the descriptor files needed by gnome-games-app

Just gambatte, bsnes-mercury-balanced and beetle-pce-fast ship the required textfiles.

See the bug link above to add those files manually if desired.

---

