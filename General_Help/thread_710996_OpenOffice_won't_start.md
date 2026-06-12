---
title: "OpenOffice won't start"
date: 2008-02-29
forum: General Help
---

### Post by Jojan on 2008-02-29
I get splash screen and it wants to recover an unsaved... what's it called,,, anyway. And then the oowriter comes up and shuts down immediately.

---

### Post by kellemes on 2008-02-29
Please run it from the terminal and watch the output for hints..

```
oowriter
``` **or**
```
ooffice -writer
```

---

### Post by Hagar Delest on 2008-02-29
Or just try to rename your OOo user profile (~/.openoffice.org2).

---

### Post by Jojan on 2008-03-01
**oowriter:**
```
jojan@jojan-laptop:~$ oowriter

(soffice:5987): Gtk-WARNING **: Kan inte hitta temamotorn i "module_path": "aurora",
jojan@jojan-laptop:~$ X-Error: BadAlloc (insufficient resources for operation)
        Major opcode: 53 (X_CreatePixmap)
        Resource ID:  0x2c002b1
        Serial No:    3935 (3935)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging
```

**ooffice -writer:**
```
jojan@jojan-laptop:~$ ooffice -writer

(soffice:6018): Gtk-WARNING **: Kan inte hitta temamotorn i "module_path": "aurora",
jojan@jojan-laptop:~$ X-Error: BadAlloc (insufficient resources for operation)
        Major opcode: 53 (X_CreatePixmap)
        Resource ID:  0x2c002b9
        Serial No:    4092 (4092)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging
```

"Kan inte hitta temamotorn i" would translate to "Can not find the theme engine in".

The only new thing that happened when I renamed the  ~/.openoffice.org2 was that it didn't want to restore that old document. But of course, a new one came and in next start it wanted to restore that one.

---

### Post by Hagar Delest on 2008-03-01
You can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

