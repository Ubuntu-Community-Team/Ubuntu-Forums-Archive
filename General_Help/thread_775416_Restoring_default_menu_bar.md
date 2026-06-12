---
title: "Restoring default menu bar?"
date: 2008-04-30
forum: General Help
---

### Post by Rusty023 on 2008-04-30
I accidentally deleted the top menu bar of Ubuntu, how can I get it back?

---

### Post by ryanhaigh on 2008-04-30
The applications/places/system menu or the whole bar.
If its just the menus, right click on a space on the top panel and select add to panel, then find menu bar and add that to the panel. Move it to where you want (you may have to unlock other things in the way first) then lock in position.

If its the whole bar right click on the bottom one and select new panel adding the things you want as described above, you will probably want menu bar and notification area at least.

---

### Post by Rusty023 on 2008-04-30
The whole bar. I've added a new bar but I don't quite remember what was on it and I want the original one back. Any ideas?

---

### Post by Nunu on 2008-04-30
Bottom bar has the goto desktop icon. Trash bin and open applications bar. that was it as far as i remember.

---

### Post by psoplayer on 2008-04-30
Off the top of my head (on the left, from the left):
Apps/Places/System
Firefox Launcher (right click on FF in Apps menu, 'Add to Panel')
Evolution Launcher
Get Help Launcher
(then on the right, from the left)
User Switcher
System Tray
Volume Widget
Clock
Exit Button

---

### Post by ryanhaigh on 2008-04-30
The top menu bar contains the menu bar and notifaction area as mentioned above, there are also a couple of launchers which you can re-add by right clicking in the menu and selecting add to panel (or something along those lines), you will also need the volume control applet, deskbar, user switcher,clock and quit. I have tried to give their proper names but I don't use the standard bar so they may be a little different.

edit: just remember to lock them in place when you are done otherwise they may be out of order when you next login.

---

### Post by Rusty023 on 2008-04-30
Yep, had a fiddle around with it and it's all good. Got some new stuff up there like different application shortcuts, a weather thing and googly eyes that follow my mouse. Thanks for your help all. Mods close please.

---

### Post by t.rei on 2010-03-02
three lines will get you the default gnome-panels back:
in terminal execute:
```

gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```after this you will have the top and bottom gnome panel as they are when you start ubuntu the first time. :)

*edit* ok to explain:
1st line unsets the entries in your gnome configuration
2nd line removes the folders in the configuration directory
3rd kills the gnome panel process (it will come back automatically using defaults and recreating the entries in your config)

---

