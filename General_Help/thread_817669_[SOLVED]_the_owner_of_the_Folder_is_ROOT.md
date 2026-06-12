---
title: "[SOLVED] the owner of the Folder is ROOT?"
date: 2008-06-03
forum: General Help
---

### Post by mahela007 on 2008-06-03
I created a folder while I was using Samba and now i dont want that folder. when i try to delete it it ways that I am not the owner. Its properties dialog says that the owner is root. How can i delete the folder?

---

### Post by tabithaboof on 2008-06-03
Try "sudo nautilus"

---

### Post by Josey on 2008-06-03
I have thunar installed as a file browser just to run it as root to do such things.
Run this in terminal
```
sudo apt-get install thunar
```
After it's install then type
```
sudo thunar
```
and a file browser will open and have root permissions.

It applies to anything you want to run as root... just type sudo before the program name.

edit: or what he said.  :)

---

### Post by rampageoberon on 2008-06-03
If the owner is root you need to login as root to delete it. You can also do

```
sudo rm -r <dir>
```

---

### Post by rampageoberon on 2008-06-03
> **Josey said:**
> I have thunar installed as a file browser just to run it as root to do such things.
Run this in terminal
```
sudo apt-get install thunar
```
After it's install then type

and a file browser will open and have root permissions.

It applies to anything you want to run as root... just type sudo before the program name.

It is not good to run things with root permissions unnecessarily. Remember that the security of the system is based on these permissions.

---

### Post by aysiu on 2008-06-03
Please use *gksudo* with graphical applications.

```
gksudo thunar
``` instead of *sudo thunar*

```
gksudo nautilus
``` instead of *sudo nautilus*

More details here:
[http://www.psychocat.net/ubuntu/graphicalsudo](http://www.psychocat.net/ubuntu/graphicalsudo)

---

