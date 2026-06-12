---
title: "Find file by specific date"
date: 2007-10-03
forum: General Help
---

### Post by gizm0 on 2007-10-03
How do i find files by specific date? For example i'm trying to find file that was created on 1.2.2007?

---

### Post by dcstar on 2007-10-03
> **gizm0 said:**
> How do i find files by specific date? For example i'm trying to find file that was created on 1.2.2007?
```

ls -al | fgrep 2007-02-01
```

---

### Post by gizm0 on 2007-10-03
Thank you, but i have one more question:
How about if i want to move those files to different directory?

---

### Post by gizm0 on 2007-10-09
Is there anyway to do this?

---

### Post by nick_h on 2007-10-09
Have a look at the manual page for find.
```
man find
```
You can find files accessed less than an hour ago with:
```
find . -atime -1 -print
```
Look at atime, mtime and ctime.  I don't think create times are stored on an ext3 filesystem.

You can then extend the syntax to move files with -exec as follows:
```
find . -atime -1 -exec mv '{}' /newdir \;
```

Make a backup first and test the command before you use it.

---

### Post by gizm0 on 2007-10-22
Thank you :).

---

