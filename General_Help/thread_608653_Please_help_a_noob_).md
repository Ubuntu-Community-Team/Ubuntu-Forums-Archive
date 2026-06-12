---
title: "Please help a noob :)"
date: 2007-11-10
forum: General Help
---

### Post by Kuniaq on 2007-11-10
Hello
I have a small problem i want to delete some files from a windows xp partition using the Ubuntu LliveCD but when i try to delete the files it says XXXX Cannot be deleted becouse its a read-only disk is there a way to delete this file? how can i make this file my 'own'

---

### Post by humungous on 2007-11-10
That's a common problem.

In a terminal, type

```
sudo gedit /etc/fstab
```

Now, search the line in which your FAT32-partition is mounted, and change the bold mount-options. Note that after that, *everyone* is permitted to write to this partition.

```
/dev/Y /media/X vfat **users,owner,ro,umask=000 0 0**
```

Save the file. To mount it without restarting, type:

```
mount -a
```

---

