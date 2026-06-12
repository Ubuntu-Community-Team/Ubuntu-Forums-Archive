---
title: "Permissions"
date: 2008-01-20
forum: General Help
---

### Post by craig88 on 2008-01-20
hey so ive been lookin through a couple posts and some say i have to edit a certain file so i go to the said file but everytime i try to edit the fle it says im not the owner and dont have permission do i have to be in root to change or is there another as ive heard using root can be dangerous?

---

### Post by banewman on 2008-01-20
The way to edit files that require root is to open a terminal (applications - accessories - terminal) and type 
gksu /path/to/file - e.g. gksu /etc/X11/xorg.conf
(gksu is used for root permission on graphical applications - sudo for non graphical)
then give your login password when asked.
:)

---

### Post by Lord Illidan on 2008-01-20
You can use sudo.

For example, in terminal :

sudo nano /etc/apt/sources.list

---

### Post by Scarath on 2008-01-20
If u want to be the owner of the file u can 'chown' it
```

sudo chown -R username /file/path/
```

just be careful with it :D

---

### Post by craig88 on 2008-01-20
cheers guys all helpfull sorted it now

---

