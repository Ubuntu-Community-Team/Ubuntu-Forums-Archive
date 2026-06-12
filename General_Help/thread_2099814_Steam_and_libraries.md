---
title: "Steam and libraries"
date: 2012-12-30
forum: General Help
---

### Post by Juniorr on 2012-12-30
Hi. Steam tray icon does not appear on Ubuntu 12.04.1 64bit. I installed all 32bit libraries (i guess) and now a user told me to type > libappindicator3-1:i386, but it wants to install brasero, brasero-cdrkit, gir1.2-appindicator3-0.1, gnome-settings-daemon, indicator-application, indicator-sound, libappindicator3-1, libbrasero-media3-1, libindicator3-7, network-manager-gnome, transmission-gtk and vino.

Whats this library for? Is it safe to install? Will it replace all software that are already installed such as brasero?

More here:[http://steamcommunity.com/app/221410/discussions/0/846940248787695011/](http://steamcommunity.com/app/221410/discussions/0/846940248787695011/)

---

### Post by thnewguy on 2012-12-30
It probably wants to install 32-bit versions of the programs alongside the 64-bit versions. Could you post the exact output apt-get is giving you?

---

### Post by Juniorr on 2012-12-30
Turns out I already have it, I looked it up on Software Center. Installing "sudo apt-get install ia32-libs" installs it too.
Thanks

---

