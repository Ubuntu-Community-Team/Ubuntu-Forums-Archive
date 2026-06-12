---
title: "2 Questions."
date: 2006-08-17
forum: General Help
---

### Post by Patrick-Ruff on 2006-08-17
hey all, I want to keep this short and simple so here's what my questions are...

Is it possible to password folders? like for instance a folder within my Home folder, is it possible to add a password to that?


second question, I've added/enabled all repository's that would involve compiz and I do sudo apt-get update and yet it STILL says it cannot find package gset-compiz, anyone know whats going on here?



thanks

---

### Post by hashimoto on 2006-08-17
Don't know about actual password, but you can right click on the folder, select properties, go to permissions and clear the tick on other users read permissions. This way only you (user) and root can see what's inside.

---

### Post by peabody on 2006-08-17
> **Patrick-Ruff said:**
> hey all, I want to keep this short and simple so here's what my questions are...

Is it possible to password folders? like for instance a folder within my Home folder, is it possible to add a password to that?


I might be able to give you better advice if you can give me a bigger picture of why you'd want to password a folder.  I assume it's so other users on the same machine can't view the folder?  There are so many different ways to "lock" a folder as it were, both easy and hard with various levels of security.  What kind of protection are you looking for?

> 
second question, I've added/enabled all repository's that would involve compiz and I do sudo apt-get update and yet it STILL says it cannot find package gset-compiz, anyone know whats going on here?


A lot of weird stuff's seems to be going on with the repositories lately.  I've attached the deb I have of it, gzipped.  Let me know if you have trouble installing it.

---

### Post by 23meg on 2006-08-17
> **Patrick-Ruff said:**
> 
Is it possible to password folders? like for instance a folder within my Home folder, is it possible to add a password to that?
[Locked Folders for Nautilus]("http://www.gnome.org/projects/nautilus-locked-folders/") seems to be what you're looking for, but it's still beta so you should judge if you should rely on it for actual use.
> 
second question, I've added/enabled all repository's that would involve compiz and I do sudo apt-get update and yet it STILL says it cannot find package gset-compiz, anyone know whats going on here?Post a copy of your sources.list .

---

### Post by Patrick-Ruff on 2006-08-17
yeah as far as the locked folders, I was referring to within the owner's account as well as any other account. because people may get on this comp at times and there are things I don't want people accessing and such. so yes, more like encrypting folders but oh well, I'll try that natilus thing.

---

### Post by Patrick-Ruff on 2006-08-17
that locked folders gnome project doesn't have a reliable server apparently, got a 404 error.

edit: thanks peabody, the gset-compiz package worked perfectly.

---

### Post by yopnono on 2006-08-17
> **Patrick-Ruff said:**
> that locked folders gnome project doesn't have a reliable server apparently, got a 404 error.

edit: thanks peabody, the gset-compiz package worked perfectly.

You can find it here.
[http://ftp.osuosl.org/pub/FreeBSD/ports/local-distfiles/pav/nautilus-locked-folder-1.0.0.tar.gz](http://ftp.osuosl.org/pub/FreeBSD/ports/local-distfiles/pav/nautilus-locked-folder-1.0.0.tar.gz)

Also if you only want other users to not view you folder, set permission to you only.

If you like to encrypt files, then use gnugpg/gpa or ccrypt and nautlilus script for frontend.

[http://ccrypt.sourceforge.net/](http://ccrypt.sourceforge.net/)
[http://www.comnet.be/files/ccrypt/ccrypt_gui_integration.zip](http://www.comnet.be/files/ccrypt/ccrypt_gui_integration.zip)

---

