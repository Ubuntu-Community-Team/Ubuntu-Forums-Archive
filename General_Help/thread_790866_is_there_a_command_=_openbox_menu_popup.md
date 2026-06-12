---
title: "is there a command = openbox menu popup?"
date: 2008-05-11
forum: General Help
---

### Post by chris4585 on 2008-05-11
I'm on openbox and I'm curious to know if there is a command to launch the Openbox menu... please let me know

---

### Post by theadmiral on 2008-05-29
get obconf from synaptic

---

### Post by dagnabit dang doohickey on 2008-05-29
If you're asking about a keyboard shortcut that will pop up the openbox menu in the same manner that a right mouse click does, I added the following keybinding to my rc.xml file to do just that.
```
  <keybind key="Menu">
    <action name="ShowMenu"><menu>root-menu</menu></action>
  </keybind>

```
Pressing the *menu key* will now pop up the openbox menu.

---

### Post by eriqjaffe on 2008-05-29
obconf won't let you launch the menu.

Built-in, just right-click on the desktop.  You can also bind it to a keystroke, but I"m not sure if the default setup has that.

What I've also done is use xdotool to allow me to call the Openbox menu from a panel:

[http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/](http://crunchbang.org/archives/2008/03/14/invoke-openboxs-menu-with-xdotool/)

---

### Post by chris4585 on 2008-05-30
Well i was looking up a way to click on a launcher to launch the openbox menu from fbpanel

eriqjaffe i'll check your link out

EDIT: looks like what i was looking for, thank you :)

---

