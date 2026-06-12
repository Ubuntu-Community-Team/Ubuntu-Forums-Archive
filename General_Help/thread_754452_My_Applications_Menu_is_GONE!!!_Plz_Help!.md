---
title: "My Applications Menu is GONE!!! Plz Help!"
date: 2008-04-13
forum: General Help
---

### Post by ALIENDUDE5300 on 2008-04-13
You're probably not going to believe this, but when I opened the menu editor, my ENTIRE Applications menu, including the categories, disappeared! Does anyone know how to fix this? Is it a know issue? I need to know ASAP because there isn't much I can do without my applications menu... :(

---

### Post by Islington on 2008-04-13
System->Preferences->Main Menu

does this still work? If so, is the applications menu checked?

---

### Post by ryanhaigh on 2008-04-13
Are places and system still there? If not then you have removed the menubar item from the panel, just right click on the panel>add to panel>menubar. You can always access your menu using Alt+F1.

---

### Post by ALIENDUDE5300 on 2008-04-17
I found a solution but forgot to update this post, so sorry for reviving an old thread, but it might help somebody.  To fix this problem I had to delete "/.config/menus/applications.menu ". The menu then automatically regenerated itself. :)

---

### Post by denizoglu on 2008-05-02
> **ALIENDUDE5300 said:**
>  To fix this problem I had to delete "/.config/menus/applications.menu ". The menu then automatically regenerated itself. :)

I have actually never had an applications menu after a fresh install of 8.04. It seems that xfce has changed its default directory and even after finding the new directory and removing the menu.xml files, still no applications under Apps Menu.

---

