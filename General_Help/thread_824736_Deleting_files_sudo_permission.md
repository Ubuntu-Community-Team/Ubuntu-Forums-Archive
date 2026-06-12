---
title: "Deleting files sudo permission"
date: 2008-06-10
forum: General Help
---

### Post by raylistic87 on 2008-06-10
Hi, 
How do i delete files that are in trash and are protected? As in they can only be deleted by sudo?
What is the command for this?:popcorn:

---

### Post by dje on 2008-06-10
in a terminal:
```
sudo rm ~/.local/share/Trash/files/*filename*
```

hope that helps,
dje

---

### Post by drs305 on 2008-06-10
Another way to do it is to open nautilus with sudo, which allows you to delete folders and files with root (and anyone else's) permissions. It also lets you look at the files first to make sure you really want to delete them. 

To open nautilus:
```
gksudo nautilus
```

To find all Trash folders in the / partition, you can run the following. The actual deleted files are normally in the Files subfolder:

```
sudo find / -type d -iname Trash
```

---

