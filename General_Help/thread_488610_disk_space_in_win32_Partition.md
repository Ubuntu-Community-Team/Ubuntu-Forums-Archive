---
title: "disk space in win32 Partition"
date: 2007-06-30
forum: General Help
---

### Post by buzst on 2007-06-30
when I move files from ubuntu to my win XP (win32) partiition, then delete the files in winXP, Ubuntu is aware the files have been deleted but the disk space available reporting does not reflect that the files are gone. Currently, my Win XP environment shows I have 12MB disk space remaining but ubuntu shows no disk space remaining on the win32 partition. Any ideas how to get both reflecting the same available space? I have run disk check and defragged the winxp disk.

---

### Post by energiya on 2007-06-30
does
```

df -h

```
say the same?

---

### Post by buzst on 2007-06-30
yes df -h says the same. Oh sorry, typo on the first post it's 12GB not 12 MB

---

### Post by buzst on 2007-07-05
bump

---

### Post by buzst on 2007-07-06
I'm thinking that maybe running dosfsck may reindex the filesystem, but would sure like some feedback or advice before I try it.

Thanks...

---

### Post by buzst on 2007-07-10
bump

---

### Post by buzst on 2007-08-12
bump

---

