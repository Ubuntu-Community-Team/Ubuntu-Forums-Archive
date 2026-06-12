---
title: "editing sources list help"
date: 2007-05-16
forum: General Help
---

### Post by wolfen69 on 2007-05-16
when i run sudo apt-get update or try to run synaptic package manager, i get the following message: " Type '“deb' is not known on line 44 in source list /etc/apt/sources.list".  i went to open the sources list in etc/apt to remove line 44, but it says i dont have permission to make or save changes. what to do?

---

### Post by Ziox on 2007-05-16
you have to be a superuser.  so:

gksudo gedit /etc/apt/sources.list

or sudo nano /etc/apt/sources.list

btw, if you can't find the error, you can post your entire sources.list file here.

---

### Post by wolfen69 on 2007-05-16
thanks a million!!!

---

