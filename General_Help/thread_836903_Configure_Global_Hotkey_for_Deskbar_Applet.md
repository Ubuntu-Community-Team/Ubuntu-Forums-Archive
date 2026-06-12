---
title: "Configure Global Hotkey for Deskbar Applet"
date: 2008-06-22
forum: General Help
---

### Post by mctk on 2008-06-22
When I search through my Preferences -> Keyboard Shortcuts I am unable to find the hotkey for Deskbar Applet.  I would like to change the hotkey from Alt-F3 (keys too far away) to Alt-Space (launchy addict...).   Am I missing the obvious?

---

### Post by mctk on 2008-06-22
I found the option for the hotkey in the gnome configuration editor.  (in terminal type
```
gconf-editor
```
Under Apps -> Deskbar I found the option to set the hotkey.  I tried setting it to <Alt>Space however, it would not work.  It appears that <Alt>Space is already bound to the Desktop Search app.  I am unable to find the option to unset that.

---

### Post by daerko on 2008-07-03
You can unbind it in Preferences->Keyboard shortcuts
You may have to log off and back in for the new shortcut to work.

---

