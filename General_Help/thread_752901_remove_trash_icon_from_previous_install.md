---
title: "remove trash icon from previous install"
date: 2008-04-12
forum: General Help
---

### Post by bubbjane on 2008-04-12
I installed Gutsy over a previous install of PCLOS which had a trash icon on the desktop.  When I installed gutsy, I kept my /home folder and did not reformat it.  Now I have a trash icon on my desktop that I can't get rid of.  the conf file in gutsy has the trash icon unchecked, but it is still there and I would like to get rid of it.  Any help would be greatly appreciated.

---

### Post by duncan.hawthorne on 2008-04-12
the trash icon is just a .desktop file
im guessing you dont have permission to edit the file as the permission is to your old user in pclos (if you go on right click >properties you can see who the owner is and who has permission to do what)
run nautilus as a superuser, which means you now have permission to do anything
ie run in the terminal:
```

sudo nautilus

```
then browse to the desktop and delete.

sorry if you've already tried this

---

### Post by aysiu on 2008-04-12
Graphical applications launched as root should use *gksudo* instead of *sudo*, so the command would be ```
gksudo nautilus
```

By the way, I don't know (based on what the OP has said in the first post) that root privileges are needed for this.

Go to your home folder, double-click on Desktop, press Control-H to show hidden files, then delete the offending file.

---

### Post by duncan.hawthorne on 2008-04-12
if the file was hidden, this wouldnt be a problem surely

---

