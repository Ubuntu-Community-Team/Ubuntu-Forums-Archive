---
title: "Weird Problem Dont Know How to Fix Please Help"
date: 2007-10-03
forum: General Help
---

### Post by R-Dot-Yung on 2007-10-03
Ok so whenever i click on my Home Folder, Trash can, Or Computer (folder), i get a message like this

Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/home_icon_name

How do i fix this, it doesnt affect how anything works but its annoying since i touch my home folder and trash pretty regularly

---

### Post by ThrobbingBrain66 on 2007-10-03
Hit Alt+F2 and type gconf-editor into the box and hit enter

navigate to the path in the error message and you should see the 'home_icon_name key.
Right-click the key and 'unset' it.  Then recreate the key and choose 'string' as it's type.

---

### Post by R-Dot-Yung on 2007-10-04
thanks that worked, what would i do without u guys

---

