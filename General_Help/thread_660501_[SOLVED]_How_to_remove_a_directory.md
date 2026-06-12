---
title: "[SOLVED] How to remove a directory?"
date: 2008-01-06
forum: General Help
---

### Post by sofasurfer on 2008-01-06
I removed the files in the directory. Now, how do I remove the directory, as in, throw it away? And how would I have done it with files still in it?

---

### Post by WiseElben on 2008-01-06
Use this command:

> rm -rf folder_name

The -r flag means "recursive," or delete all other folders in it. The -f flag means "force," which means it won't prompt you and will delete everything.

---

### Post by yabbadabbadont on 2008-01-06
```
rmdir directoryname
```
```
rm -r directoryname
```
Edit: Too slow.

---

### Post by sofasurfer on 2008-01-06
This is my first day as an Ubuntu user. I just switched from Debian. And I have to say, Holy Cow!!! This is the fastest reply I have ever gotten. Thanks.

---

### Post by ryanVickers on 2008-01-06
> **sofasurfer said:**
> I removed the files in the directory. Now, how do I remove the directory, as in, throw it away? And how would I have done it with files still in it?

um, you delete it.... ?

same as every other OS, including windows... you just delete it, with or without files in it...

from the command line, rm will delete, or sudo rm if it's a root folder [B](careful with this!!)
[/B]

---

