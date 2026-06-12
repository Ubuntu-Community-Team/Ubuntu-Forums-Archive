---
title: "Filesystem"
date: 2007-04-22
forum: General Help
---

### Post by Visudo on 2007-04-22
I have just installed Feisty Forn and I am a complete newbie!

I want to install Apache/MySQL/PHP into /usr/src or /usr/local/src but i have "Read Only" permissions on the "Filesystem" (my hard drive).

When I try to change the permissions from "Read Only" to "Read and Write" I get "The Permissions could not be changed"

How can I change the permissions so that I can save and install files?

Ste

---

### Post by chrisccoulson on 2007-04-22
In a terminal, try:

```
gksudo nautilus
```

Also check out [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Visudo on 2007-04-22
I get the following error message:

(gksudo:15066): Gtk-WARNING **: cannot open display:

---

### Post by Slim Odds on 2007-04-22
> **Visudo said:**
> I have just installed Feisty Forn and I am a complete newbie!

I want to install Apache/MySQL/PHP into /usr/src or /usr/local/src but i have "Read Only" permissions on the "Filesystem" (my hard drive).

When I try to change the permissions from "Read Only" to "Read and Write" I get "The Permissions could not be changed"

How can I change the permissions so that I can save and install files?

Ste

Those locations require "root" access. Use : sudo to get access. ```
sudo cp <source> <dest>
```just enter your password when prompted.

---

### Post by chrisccoulson on 2007-04-22
-

---

### Post by Visudo on 2007-04-22
Stupid question!

What do I put for <source> and <dest> ?

Ste

---

### Post by Visudo on 2007-04-22
bump

---

### Post by Slim Odds on 2007-04-22
Simply put, sudo <command args> runs anything as root. So use sudo to run whatever you need to access protected areas of the drive or to run services that need root access. If it's GUI application and you're using GNOME, use gksudo.

---

