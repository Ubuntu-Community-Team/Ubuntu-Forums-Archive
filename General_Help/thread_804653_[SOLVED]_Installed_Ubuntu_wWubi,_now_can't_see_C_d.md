---
title: "[SOLVED] Installed Ubuntu w/Wubi, now can't see C: drive"
date: 2008-05-23
forum: General Help
---

### Post by nubyrchrd on 2008-05-23
When I used the live cd, I could see all of my windows files on the c drive, but now cannot. Can someone help?

---

### Post by abn91c on 2008-05-23
look in /host

---

### Post by jackhe22 on 2008-05-28
Sorry if this is dumb, but how do you get to /host?

---

### Post by wootah on 2008-05-28
Open a terminal (Accessories -> Terminal) and type
```

cd /host
ls

```That will show you all of the files and directories in /host. From the GUI, Open Nautilus (ALT - F2) type *nautilus* and browse to /host.

EDIT: No question is dumb, that's why the forums are here for you :)

---

### Post by ShangTsungOmega on 2008-05-28
Alternatively you can also browse to it inside of gnome or kde gui by going to places, computer, file system, host. Keep in mind its read only so you won't be able to modify files there but you can copy,paste files from it to anywhere else you can write files to.

---

