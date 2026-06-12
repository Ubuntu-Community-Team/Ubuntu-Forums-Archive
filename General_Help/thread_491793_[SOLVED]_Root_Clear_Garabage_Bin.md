---
title: "[SOLVED] Root Clear Garabage Bin"
date: 2007-07-04
forum: General Help
---

### Post by jusmurph on 2007-07-04
I have files in my recycle bin that i can't remove, how do i  them because i have to skip each one of them?

---

### Post by deepclutch on 2007-07-04
Do u meant that u have files to be cleared from root trashbin or local user trash.be clear

---

### Post by jusmurph on 2007-07-04
In local trash bin.

I just can't remove them.

---

### Post by deepclutch on 2007-07-04
When ur logged in as local user(ur account),U can remove them by going to via terminal:
```
cd  ~/.Trash
```
then while in ~/.Trash,
```
sudo  rm -rf    * 
```
^ will remove the trash entries.
and terminal can be launched from right click on desktop or from GNOME menu Applications>Accessories>Terminal.

---

### Post by jusmurph on 2007-07-04
Cheers :)

---

