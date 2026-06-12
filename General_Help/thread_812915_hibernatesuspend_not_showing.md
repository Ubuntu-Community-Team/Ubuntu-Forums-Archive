---
title: "hibernate/suspend not showing"
date: 2008-05-30
forum: General Help
---

### Post by mzruya on 2008-05-30
Hey, i have a minimal ubuntu install, so i may left some packages out,
when i select "quit" on gnome i dont have the hibernate or suspend options,
is there a package which i'm missing ?

thanks,

---

### Post by MythosLegend on 2008-05-30
Let's see if this works first.

Run gconf-editor. 
Go to apps. 
Go to gnome-power-manager and expand it
Go to general. 
Make sure "can_hibernate" and "can_suspend" are checked.

---

### Post by mzruya on 2008-05-30
ok, hibernate now show's, suspend doesn't ..
and after hibernating, when i push the computer power button it starts from the boot process ...

---

### Post by mzruya on 2008-05-30
and after rebooting the settings got disabled again for some reason, maybe gnome is disabling them ?

---

