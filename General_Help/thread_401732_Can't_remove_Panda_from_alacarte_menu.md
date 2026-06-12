---
title: "Can't remove Panda from alacarte menu"
date: 2007-04-04
forum: General Help
---

### Post by 67GTA on 2007-04-04
I installed Panda Desktopsecure out of curiosity and decided it was too pushy. It reminded me too much of Windows. I uninstalled it and the menu entry is still hanging around in my alacarte menu editor. I searched for the files that might be still on the system and deleted them, but it is still there. It isn't hurting anything, just aggravating is all. Where is this thing hiding at? Is there a configuration script for alacarte that I'm missing? Where should I look?
[ATTACH]28997[/ATTACH]

---

### Post by Scruffy10 on 2007-04-09
I'm basing this off the picture you attached.

In alacarte, click on the applications entry (The parent folder of all the other menus)

Either click the checkmark for Panda or right click and select delete.

---

### Post by ardchoille42 on 2007-04-09
Most of the entries in the gnome menus are .desktop files in /usr/share/applications. Go into that directory and look for the Panda menu item and delete it. That should take that menu item out of the menus, though you may need to do a

```

killall gnome-panel

```

That will respawn the gnome panels and re-parse the menus.

---

