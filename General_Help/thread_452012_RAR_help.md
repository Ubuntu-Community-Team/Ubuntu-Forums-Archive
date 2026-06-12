---
title: "RAR help"
date: 2007-05-22
forum: General Help
---

### Post by Dave B on 2007-05-22
i just migrated from XP and have a few RAR files that were created by WINRAR.

i tried to use the RAR app that came with the install and it didnt seem to like the WINRAR file.

is there a rar utility that is graphic that i can use or try to use?

Thanks 

DAVE

UBUNTU ROCKS

:popcorn:

---

### Post by taurus on 2007-05-22
Try using the unrar to see if you can unrar those files.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install unrar
unrar x **filename.rar**
```

---

### Post by bashologist on 2007-05-22
Then after installing unrar you could try "file-roller" for gnome, or "ark" for kde. These are general apps for managing archives graphically tho so you won't get anything like winrar for windows. You could check their site; they might have something graphical for linux specifically for rar.

---

### Post by zvacet on 2007-05-23
```
sudo aptitude install rar unrar p7zip p7zip-full
```

Just right click on rar package and select **unpack here**.You don´t need GUI for that.

---

