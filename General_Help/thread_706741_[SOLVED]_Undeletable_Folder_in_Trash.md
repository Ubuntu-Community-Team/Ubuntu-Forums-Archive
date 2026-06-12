---
title: "[SOLVED] Undeletable Folder in Trash"
date: 2008-02-24
forum: General Help
---

### Post by TechShep on 2008-02-24
I was recently trying to create a live disk from my current setup, but when I was copying the files to the .ext2 file, I ran out of space to finish. I sent it to the trash, (including the folder above it) but then when I try to empty the trash, it just tells me that it cant be deleted :( I am pretty sure the problem is caused by the fact that what I am trying to delete is an empty folder that takes up 3 GB of space (after emptying the trash, it shows as a folder instead of a .ext2 file)

Any hints on how to delete this?

---

### Post by Beefeater on 2008-02-24
First of all have you tried to delete it as root?

---

### Post by wireddad on 2008-02-24
In Terminal:
>cd ${HOME}/.Trash
>sudo rm -ri *

Had to use this just last night.

[http://ubuntuforums.org/announcement.php?f=131](http://ubuntuforums.org/announcement.php?f=131)

---

### Post by LaRoza on 2008-02-24
The "f" option is dangerous, the "i" will prompt you before doing anything, so you know exactly what is being deleted.

---

### Post by wireddad on 2008-02-24
> **LaRoza said:**
> The "f" option is dangerous, the "i" will prompt you before doing anything, so you know exactly what is being deleted.

Thank you.

---

