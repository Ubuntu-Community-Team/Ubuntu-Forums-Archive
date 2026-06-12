---
title: "pop-up panel. remove desciption"
date: 2006-11-25
forum: General Help
---

### Post by falkenberg_cph on 2006-11-25
Hi
I have made myself a panel that is hidden in the bottom of my desktop. Its nothing fancy, no docker, no beryl - just a plane gnome panel.

At the moment my icons contain a description that i would like to get rid of.
I confuses more than it does any good.
I can right click the icon, and choose properties, there i can see the description. But when i delete it and close. it comes back again.

Are there anyway to permanently remove the description.

I hope you understand what i was trying to explain
Thanks in advance
/Carsten

---

### Post by CatKiller on 2006-11-25
**gconf-editor**
/apps/panel/global/tooltips_enabled

might be what you're looking for.

---

### Post by bapoumba on 2006-11-25
Hi,

these are tooltips. Just open gconf-editor :
apps > panel > global

Uncheck "tooltips_enabled" (next to last)

I also use simple gnome-panel ;)

---

### Post by falkenberg_cph on 2006-11-27
thank you both :)  - works well

/carsten

---

