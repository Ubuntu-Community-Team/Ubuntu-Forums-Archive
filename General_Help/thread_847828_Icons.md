---
title: "Icons"
date: 2008-07-02
forum: General Help
---

### Post by esullivan on 2008-07-02
I downloaded an icon theme from gnome-look:
[http://www.gnome-look.org/content/show.php/Mac_OS_X_Leopard_for_Ubuntu_v1.0?content=73271](http://www.gnome-look.org/content/show.php/Mac_OS_X_Leopard_for_Ubuntu_v1.0?content=73271)

When I installed it from the theme screen, it changed some of the icons but not a couple of things like folders.

Any help?

---

### Post by esullivan on 2008-07-02
OK so I guess the icon paths change in 2.22 gnome.  Any ideas how to make it work?

---

### Post by VargasTheBlind on 2008-07-03
Same problem here, different theme.

---

### Post by vishzilla on 2008-07-03
Well they have to be repackaged...I suggest you use Mac4Lin icons found in Gnome-look

---

### Post by ITom on 2008-07-06
You have to unpack icon package, then run Alt+F2 gksudo nautilus. Go to icon folder location, right mouse click on it Properties, Permissions. Change to Owner (Folder access - Create and delete files, File access - Read and Write), Group (Folder access - Access files, File access - Read only), Others (Folder access - Access files, File access - Read only). Uncheck EXECUTE. So, permission to all folders and subfolders sould be 755, for all files - 644. (you can check this in terminal ls -al YOU ICONS FOLDER). After changing permission in terminal run 'sudo cp -R \home\YOUR LOGIN\PATH TO ICONS FOLDER\ICON FOLDER NAME \usr\share\icons' This command make copy Icons Folder to main system icons location (I preffer this to see changes in root (Administrative) application)

---

### Post by hackerseraph on 2008-07-06
errrm i think i would go with the 2.22 incompatability; your best off repackaging them or just finding another set

---

### Post by gdp77 on 2008-07-08
Similar problem here. I use compiz with emerald theme manager and I cannot change the **ICON THEME** from system--->preferences--->appearance. I can choose the "default" icons mist, human, etc. , but no change will happen if I choose a downloaded theme like snow apple, noia, stylish etc. (some icons do change, but folder icons remain the shame)

Anyone has any idea what to do?

---

