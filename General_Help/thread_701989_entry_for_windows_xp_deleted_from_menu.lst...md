---
title: "entry for windows xp deleted from menu.lst.."
date: 2008-02-19
forum: General Help
---

### Post by Mia_tech on 2008-02-19
after running an upgrade on my system, the entry for my windows xp was deleted from the menu.lst file in grub... does anyone know how to recover my old file or how to put this entry back on the menu.lst file

thanks

---

### Post by northern lights on 2008-02-19
Open a terminal, type ```
sudo gedit /boot/grub/menu.lst
``` and at whatever position in the bootmenu you want XP to appear add ```
title		Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

