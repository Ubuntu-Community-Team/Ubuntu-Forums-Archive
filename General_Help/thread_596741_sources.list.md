---
title: "sources.list"
date: 2007-10-29
forum: General Help
---

### Post by debeyt on 2007-10-29
I inadvertently put some garbage data in the etc/apt/sources.list file. I cannot seem to edit this file (permission problems) to remove the offending entries. Is there any way I can set the permissions so that either I can edit this file or replace it? Until I do, I am not able to run Aptitude nor the Add/Remove program.

Thanks

---

### Post by taurus on 2007-10-29
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Maestro23 on 2007-10-29
> **debeyt said:**
> I inadvertently put some garbage data in the etc/apt/sources.list file. I cannot seem to edit this file (permission problems) to remove the offending entries. Is there any way I can set the permissions so that either I can edit this file or replace it? Until I do, I am not able to run Aptitude nor the Add/Remove program.

Thanks

You need** sudo or gksudo**.

If using gedit:

> gksudo gedit /etc/apt/sources.lst

Make your changes and save.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by debeyt on 2007-10-29
working on it now. Much appreciated

---

### Post by MrFSL on 2007-10-29
If you are interested in the GUI method

From the toolbar click:

System > Administration > Software Sources

---

