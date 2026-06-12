---
title: "No application menu icons visible in 16.04"
date: 2016-04-24
forum: General Help
---

### Post by j.p5r on 2016-04-24
I'd like to see the icons in application menu for better navigation (for example in Writer, File -> New should have it's own icon)

Back in 14.04 there was this setting: ```
gsettings set org.gnome.desktop.interface menus-have-icons true
``` and ```
gsettings set org.gnome.desktop.interface buttons-have-icons true
``` but it does not work any more.

I've also tried ```
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides "{'Gtk/ButtonImages': <1>, 'Gtk/MenuImages': <1>}" 
```but it does not work either.

Any other ideas?

---

### Post by j.p5r on 2016-04-24
Meantime I've found that it is related to this: [https://bugs.launchpad.net/inkscape/+bug/1401307](https://bugs.launchpad.net/inkscape/+bug/1401307)

If I run inkscape with the [COLOR=#333333][FONT=monospace]UBUNTU_MENUPROXY=0 inkscape [/FONT][/COLOR] command, then the icons are visible.
But that requires to run every application with such command and is not good long-term solution.

---

