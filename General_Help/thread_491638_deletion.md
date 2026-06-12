---
title: "deletion"
date: 2007-07-03
forum: General Help
---

### Post by mr.farenheit on 2007-07-03
how do i delete a file that says i don't have the right permission because i am not the owner. i tried to install ntfs-3g using fuse and found another way to install it without the use of fuse. i had several failed attempts to install fuses' tar.gz file before i found the alternative but now i have files in my trash that won't let me delete them do to lack of permission. please help:(

---

### Post by southernman on 2007-07-03
The easiest way is to open a terminal window and cd into the trash directory you want to delete from, then do...

> sudo rm <file1 file2>

That should get ya squared away.

---

### Post by Jem00 on 2007-07-03
hey,

Try this

```
sudo rm -rf ~/.Trash/*
```

---

### Post by southernman on 2007-07-03
> **Jem00 said:**
> hey,

Try this

```
sudo rm -rf ~/.Trash/*
```
I stand corrected (although it was the easiest way I knew how), this is the easiest way! ;)

---

