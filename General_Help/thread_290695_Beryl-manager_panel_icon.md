---
title: "Beryl-manager panel icon"
date: 2006-11-01
forum: General Help
---

### Post by patr547 on 2006-11-01
I just installed beryl, and i accidentally removed the icon for it from the panel, so now I can't access the manager's menu..anyone know how to get this back on? :(

---

### Post by Forge42 on 2006-11-01
> **patr547 said:**
> I just installed beryl, and i accidentally removed the icon for it from the panel, so now I can't access the manager's menu..anyone know how to get this back on? :(


Enter 'beryl-manager' into a terminal prompt.

---

### Post by BLTicklemonster on 2006-11-01
I think, in the meantime while you wait for someone to tell you how to just add a launcher, you can open terminal and type

beryl-manager

to get beryl up.

(I think that may be the actual command you type in if you want to create your own launcher. sorry, I'm not on a linux box at the moment)

---

### Post by strabes on 2006-11-01
If you mean the notification area icon, then just run beryl-manager either with alt+f2 or in a terminal.

If you mean a launcher, right click on a blank area on the panel, hit add to panel, and then at the top of the new window, hit custom application launcher. In the Command box, type beryl-manager. The beryl icons are located in /usr/share/pixmaps. You should probably use /usr/share/pixmaps/beryl-manager.png

Hope this fixes your problem.

---

### Post by patr547 on 2006-11-01
> **strabes said:**
> If you mean the notification area icon, then just run beryl-manager either with alt+f2 or in a terminal.

If you mean a launcher, right click on a blank area on the panel, hit add to panel, and then at the top of the new window, hit custom application launcher. In the Command box, type beryl-manager. The beryl icons are located in /usr/share/pixmaps. You should probably use /usr/share/pixmaps/beryl-manager.png

Hope this fixes your problem.

that's it, thanks!

---

### Post by BillGod on 2006-11-01
if you want the manager to start up every time you log in. click on system\preferences\sessions click on startup then add beryl-manager to the list.

---

### Post by Xanatos Craven on 2006-11-16
I added beryl-manager to the startup programs, but every time I do that, it doesn't save the changes. Is that supposed to happen?

---

