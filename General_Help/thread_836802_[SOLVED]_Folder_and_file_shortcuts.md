---
title: "[SOLVED] Folder and file shortcuts?"
date: 2008-06-21
forum: General Help
---

### Post by Ryklou on 2008-06-21
how do you create shortcuts?

tnx

~francois

---

### Post by drs305 on 2008-06-21
Click and drag for many.
Right click and "Add to Panel" for the top and lower panels (or drag).

It depends on what you are trying to accomplish. If this didn't answer your question, give us some specifics of what you would like to do and we can help you.

---

### Post by Ryklou on 2008-06-21
i'm trying to make a shortcut so i can put it on my desktop.

i need '/opt/lampp/htdocs/' on my desktop, so i can access it easier.

---

### Post by Ryklou on 2008-06-21
so nobody wants to answer?

---

### Post by drs305 on 2008-06-21
> **Ryklou said:**
> i'm trying to make a shortcut so i can put it on my desktop.

i need '/opt/lampp/htdocs/' on my desktop, so i can access it easier.

Been away and am surprised no one has provided the answer. 

If it's a root-owned file/folder, open nautilus as root:
```
gksudo nautilus
```

Find the file/folder.
Right click the file/folder you want to make a shortcut for; Make Link
Drag the link to the desktop and release.

If you own the file, just open a regular version of nautilus; sudo isn't required.

You can make a link via terminal with:
```
 sudo ln -s /opt/lampp/htdocs/ ~/Desktop

```


I don't know if the sudo is required for root-owned files. You can try it without. Also, this creates a soft link. There are also hard links. You can do a search for the difference.

---

### Post by cariboo on 2008-06-21
Have you tried making a symlink, something like:

```
ln -s /opt/lamp/htdoc ~/Desktop
```

This actually links directly to the directory. If you can't find the "~", on my keyboard it is to the left of the 1 key.

Jim

---

### Post by Ryklou on 2008-06-21
ok, ty

---

