---
title: "K-Torrent"
date: 2008-05-13
forum: General Help
---

### Post by abbasali31 on 2008-05-13
I installed K-Torrent successfully, and was working fine.  Today, after rebooting Ubuntu, Ktorrent disappeared from Application/Accessories menu. I know it is still installed because just to check when I ran this command from terminal:

sudo apt-get install ktorrent

The message appeared that Ktorrent is running a updated version.

Why is it disappeared from Application/Accessories Menu?

---

### Post by zenwalker on 2008-05-13
Not sure what hapnd. But u can have it back. Right click on the menu items and create new entry and add. 

Probably a file corrupt regarding that entry. Just log off and back on. Is it back?

---

### Post by abbasali31 on 2008-05-14
It didn't work.  perhaps, I should just uninstall ktorrent and then reinstall it.

Whould be the uninstall command from terminal.

Thanks,

---

### Post by maybeway36 on 2008-05-14
What you sohuld probably do ins remove and purge it:
```
sudo apt-get remove --purge ktorrent
```
then install it again:
```
sudo apt-get install ktorrent
```

---

