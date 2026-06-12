---
title: "How to delete changes made with Install command"
date: 2021-11-28
forum: General Help
---

### Post by shadysand on 2021-11-28
Hello,

ive tried to install cli gdrive with sudo install gdrive /usr/local/bin/gdrive but decided to skip it and im trying to currently delete gdrive variable from system that was created with that command, ive deleted usr/local/bin/gdrive directory, but using gdrive still points to usr/local/bin/gdrive and gives -bash: /usr/local/bin/gdrive: No such file or directory information.

Any way to reverse changes made by install command?

---

### Post by slickymaster on 2021-11-29
*Thread moved to **General Help**.*

---

### Post by T6&amp;sfpER35% on 2021-11-29
```
sudo apt-get --purge remove gdrive
```
```
sudo apt-get autoremove
```

see if that does the trick ?

---

