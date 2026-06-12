---
title: "Gnome fallback (compiz) problem"
date: 2014-04-25
forum: General Help
---

### Post by adbiz on 2014-04-25
Okay. I was fiddling with the settings in Gnome fallback. The end result is that the Unity interface now appears on top of the GDM. Anyone know how to get rid of the Unity and have the Gnome desktop back? It seems that this problem appears in both Gnome fallback compiz and metacity.

it might have had something to do with me setting SETSID UNITY

Thx.

---

### Post by deadflowr on 2014-04-25
You need to go into compizconfig-settings-manager, then click on the unity shell plugin,or whatever it's called, and uncheck it to disable unity.(the check box is on the left side pane)

After that, it should stay disabled when running gnome-flashback.
Though, if you switch to unity, it might need to be re-enable.
But I think, it will stay disabled for the gnome-flashback side.
At least it did for me when I had to reset it once before.

---

### Post by adbiz on 2014-04-25
that worked.
thanks.

---

