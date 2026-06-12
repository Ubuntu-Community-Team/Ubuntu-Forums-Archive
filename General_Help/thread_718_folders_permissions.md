---
title: "folders permissions"
date: 2004-10-15
forum: General Help
---

### Post by tanari on 2004-10-15
How change folder permissions (include subfolders)? 
I know, that I can press right mouse button and change permissions, but
permissions change only for one folder. In KDE Konqueror was function to
select "change in subfolders too" (or something like taht), but in gnome
I didn't find this function.

---

### Post by ubuntu-geek on 2004-10-15
from a terminal window you can do, I'll use 755 for an example:

chmod -R 755 folder

that will set the permissions to 755 for all the files in that folder.

---

### Post by tanari on 2004-10-15
for subfolders too?

---

### Post by normnmiles on 2004-10-15
yes.  The switch -R is for recursive or everything under that folder.

---

### Post by tanari on 2004-10-16
thanks

---

