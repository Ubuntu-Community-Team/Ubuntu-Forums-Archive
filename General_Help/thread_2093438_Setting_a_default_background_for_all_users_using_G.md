---
title: "Setting a default background for all users using Gnome 3"
date: 2012-12-10
forum: General Help
---

### Post by smr42192 on 2012-12-10
I'm currently trying to set a wallpaper image as the default background for all users who log-in. I know with Gnome 2 this could be done using gconf settings. How would one do this using Gnome 3? I have tried installing fallback and running Gnome 2 and the following command:

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type string --set /desktop/gnome/background/picture_filename usr/share/backgrounds/filename.jpg

This ended up not working for me.

---

