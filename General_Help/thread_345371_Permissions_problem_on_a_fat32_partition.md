---
title: "Permissions problem on a fat32 partition"
date: 2007-01-24
forum: General Help
---

### Post by Gargamella on 2007-01-24
I have a dual boot laptop (xp and ubuntu) and i use a fat32 partion to share data between systems.
I don't know why now I am not able to edit 2 folders on that (music and download)
Do you know anything about it?

How should I do to stop that? (just changing permissions or using different folders for each system?)

---

### Post by mizar001 on 2007-01-24
Look at the granted permissions and users/groups that have access to these folders. With what user are you logged in Ubuntu?

---

### Post by Gargamella on 2007-01-24
Yes my problem is when in ubuntu.With Windows no problem.

The problem is that they became only accessible by root, so I can't do anything by nautilus

---

### Post by Pobega on 2007-01-24
Can't you just run nautilus as root? Alt+F2 and type> gksudo nautilus /mnt/hdsubstituting the /mnt/hd for your FAT32 partition's mount point.

**Edit:** Now that I think about it, shouldn't this thread be in a support section?

---

### Post by Brunellus on 2007-01-24
thread moved to general support in the hopes that it catches the right eyeballs.

---

### Post by Gargamella on 2007-01-24
yes uou're right, I should have put it in support section....

...anyway there is no possibility to make these 2 folders exec to all users?

---

