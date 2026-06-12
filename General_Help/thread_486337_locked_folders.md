---
title: "locked folders"
date: 2007-06-27
forum: General Help
---

### Post by tater_3001 on 2007-06-27
i have two folders on my desktop that have the lock symbol on them and they are both trash but i cannot delete them nor sign into root from the login window for some reason... does anyone kno how to delete them using terminal if it is possible

---

### Post by speaker219 on 2007-06-27
if you want to delete everything in your trash, including things that are locked, enter this command in the terminal:
```
sudo rm -Rdf ~/.Trash/*
```
that will delete everything in your trash folder

---

### Post by tater_3001 on 2007-06-27
they are on my desktop i need to put them in the trash...

---

### Post by se7en on 2007-06-28
try one of these

sudo chmod 777 -R nameoffile
or
sudo chown -R yourusername nameoffile

either one should give you enough permission to delete the file

---

### Post by speaker219 on 2007-06-28
> **tater_3001 said:**
> they are on my desktop i need to put them in the trash...
then use "sudo rm [the file you want to delete]"

---

