---
title: "Cannot remove icons or file from Desktop"
date: 2007-11-05
forum: General Help
---

### Post by explorer716 on 2007-11-05
I have two application start-up icons and icon that looks like a file folder with a padlock that I cannot delete  from my Desktop.  When I try to delete them I get this error message, "Cannot remove "home/robe...nions" to the trash because you do not have permissions to change it or its parent folder."


I am running Ubuntu 7.10.

You assistance will be appreciated.

---

### Post by Maestro23 on 2007-11-05
> **explorer716 said:**
> I have two application start-up icons and icon that looks like a file folder with a padlock that I cannot delete  from my Desktop.  When I try to delete them I get this error message, "Cannot remove "home/robe...nions" to the trash because you do not have permissions to change it or its parent folder."


I am running Ubuntu 7.10.

You assistance will be appreciated.

Open a terminal. Can you:

> cd ~/Desktop

then

sudo rm -r (folder in question)

---

### Post by lyndaj70 on 2007-11-05
open a terminal and type:
```
su nautilus
```
this will ask you for your password.  Then use nautilus to cut the file (edit, cut) then, making sure to keep in the same instance of nautilus, go to /home/ (your username here).  Paste the files there...

Or you can simply delete the files in nautilus...  I found it easier to run nautilus as superuser (su) while learning linux, cause that makes it more like familiar gui territory....

Take care!
~Lynda

---

