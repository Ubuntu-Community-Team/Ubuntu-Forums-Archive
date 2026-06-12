---
title: "Remove gnome-panel"
date: 2008-07-09
forum: General Help
---

### Post by unabatedshagie on 2008-07-09
I'm running avant, gnome-do and stand alone tray so I have no need for gnome panel running at all.

Could someone explain how to stop gnome panel starting when I log in?

---

### Post by tamoneya on 2008-07-09
cant you just right-click on it and say remove this panel.  Do it for both and you should be set.

---

### Post by unabatedshagie on 2008-07-09
Nope, you can't delete/remove the last panel.

---

### Post by sayakb on 2008-07-09
Open Session preferences: System->Preferences->Session->Current Session tab and change the **Style** of gnome-panel to **Trash.** Now at a terminal, do:
```
killall gnome-panel
```
Now at session preferences, click on Session Options tab and **check **the "Auto remember...." checkbox and restart X (Ctrl+Alt+Bkspace)

---

