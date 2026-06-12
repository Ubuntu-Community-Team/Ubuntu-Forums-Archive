---
title: "System Halt"
date: 2008-01-26
forum: General Help
---

### Post by MacLellan on 2008-01-26
My system is coming to a halt,
and I believe it is because of the screen saver, specifically the braid screen saver.

my problem also is that the system halts when I open the screen saver screen 
so this is leaving me unable to change my screen saver back to none.

is there a command I can type in order to switch my screen saver to something else ?

---

### Post by diaa on 2008-01-26
To restore screensaver to blanking only you can run the following command:
```
gconftool-2 --type string --set /apps/gnome-screensaver/mode blank-only
```Alternatively you can do it manually by running
```
gconf-editor
```then in the tree to the left go to apps/gnome-screensaver, then on the right panel set the *mode* key to [I]blank-only

-- 
Diaa Sami
[/I]

---

