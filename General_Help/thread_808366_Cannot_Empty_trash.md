---
title: "Cannot Empty trash"
date: 2008-05-26
forum: General Help
---

### Post by Vrekk on 2008-05-26
OK there are files in my trash can that i just cant delete.  It says PERMISSON DENIDED wen i try can anyone help?

---

### Post by TeoBigusGeekus on 2008-05-26
```
sudo rm -r /home/yourusername/.local/share/Trash/files/*
```

---

### Post by sisco311 on 2008-05-26
The Trash folder is a hidden folder(the folders name begins with a period) in your home directory.
You can press Ctrl+H in nautilus or select Show Hidden Folder from the View menu to list the hidden folders.

You probably moved some files owned by root to the trash and now you don't have permissions to delete the files.
You need to delete the files as super-user. 

To open nautilus (as super-user) in the .Trash folder
press Alt+F2 and type:
```
gksu nautilus ~/.Trash
```In Hardy Heron(8.04) the Trash is in ~/.local/share/Trash/files/

```
gksu nautilus ~/.local/share/Trash/files/
```Or delete the content of the folder from the terminal:

```
sudo rm -fr ~/.Trash/*
```Hardy Heron(8.04):
```
sudo rm -fr ~/.local/share/Trash/files/*
```

---

### Post by Vrekk on 2008-05-26
thanks, that was really starting to piss me off

---

