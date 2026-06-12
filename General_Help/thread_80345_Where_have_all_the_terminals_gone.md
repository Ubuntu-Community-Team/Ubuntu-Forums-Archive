---
title: "Where have all the terminals gone?"
date: 2005-10-22
forum: General Help
---

### Post by MasterXandrex on 2005-10-22
:confused: :confused: :confused: :confused: 

I am relatively new to Linux, and have recently upgraded to Breezy from Hoary(5.04 -- not sure of the name). Anyway... the first thing I noticed... the terminals are gone... I cannot open a terminal inside the GUI. I usually right click>open terminal   <-- removed. So, I thought that maybe they had simply removed that particular shortcut... until I found that is was not in any of my menus. It seems, the only way i can access a terminal is through the virtual workspaces (Ctrl+Alt+F?). Secondly, I found that many of the standard developer tools were gone... like "make".

What's going on? I need these things... is there a package or something to reenable these items...?

Like I said, I am relatively new, but I thought that these things were pretty standard... anyone know?

If I cannot get these items, I will have to switch distro's (something I would not like to do seeing as how I really like Ubuntu).

---

### Post by aysiu on 2005-10-22
For Breezy, for some odd reason, Terminal moved from System Tools to Accessories, but it's there. If, for some reason, you can't find it in Accessories, use the menu editor to create a new menu item with the command ```
gnome-terminal --working-directory=%f
``` If you want standard developer tools ```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Corvillus on 2005-10-24
Also, if you want "Open Terminal Here" on the context menu, you can use
```
sudo apt-get update
sudo apt-get install nautilus-open-terminal
killall nautilus
```
Nautilus should restart and you should have the open terminal option on the context menu now.

---

