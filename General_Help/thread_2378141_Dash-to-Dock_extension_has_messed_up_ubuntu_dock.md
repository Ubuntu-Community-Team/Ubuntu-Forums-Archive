---
title: "Dash-to-Dock extension has messed up ubuntu dock"
date: 2017-11-20
forum: General Help
---

### Post by sbdesign on 2017-11-20
With a gnome session I experimented with installing dash to dock...

I decided not to use it and uninstalled it but now ubuntu dock is not full height and hides itself like dash-to-dock used to.

How can I restore ubuntu dock to its default state?

---

### Post by Frogs Hair on 2017-11-20
Try  the following. ```
sudo apt install dconf-editor 
``` navigate to org/gnome/extensions/dash-to-dock/and scroll through the settings until you locate autohide, extend hight, dock fixed , and intelligent hide and adjust accordingly. Dash to dock is just a front end for settings that are available in the dconf editor.

---

