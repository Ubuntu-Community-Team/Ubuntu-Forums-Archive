---
title: "Resetting The Default Ubuntu Takebar Panel?"
date: 2008-06-21
forum: General Help
---

### Post by Tridion2000 on 2008-06-21
I decided to try AWN and now regret it. I couldn't work out how to get rid of the default taskbar panel so I deleted everything in it. Then I found out you could just stop gnome-panel from starting up on boot up.

However, now when I put gnome-panel back I just have a small empty panel. This causes other problems in that the updates notification and wireless signal icon appear as odd litle windows on the desktop.

How can I go back to how things were when I first installed Ubuntu? The nice clean taskbar at the top.

---

### Post by Tridion2000 on 2008-06-21
Fixed this by myself. For anyone who wants to know, delete the .gconf/apps/panels directory and gnome-panels will reset itself to its default.

---

### Post by brett123 on 2008-06-21
I just went through the same thing, however I did it manually:

Right click on the top panel, and select NEW PANEL, then just add the things back that were there (bin, workspace switcher etc).

---

