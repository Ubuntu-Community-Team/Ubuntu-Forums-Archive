---
title: "Access Denied"
date: 2008-05-22
forum: General Help
---

### Post by zyxyellowxyz on 2008-05-22
I have previous applications that I have downloaded, and after deciding not to install them, I deleted the extracted contents. (They were in a tar.gz file, I extracted the contents, and then deleted them.)
Now, whenever I try to fully empty my trash, I get the following error:

```
Access denied to /home/susan/.local/share/Trash/files/(file name(s))
```

The size, with the files that can't be permanently deleted, is now 6.2 MB
With 341 files and 178 sub-folders.

:confused:

Does anyone know how to solve this problem?

---

### Post by Iowan on 2008-05-22
You could try using **sudo**. You might also **ls -al** to see if the files are read-only.  If that's the case, you could change the attributes to allow you to delete them.

---

### Post by Patb on 2008-05-22
In a terminal this should do it:
```
sudo rm -r /home/susan/.local/share/Trash/files/*
```
If you are a beginner, start that way.  That will confirm deletion for each file and directory.  If you are confident you want everything deleted, make it:
```
sudo rm -rf /home/susan/.local/share/Trash/files/*
```
This command will permanently delete everything in /home/susan/.local/share/Trash/files/ without confirming so take care.  

Cheers, Pat.

---

