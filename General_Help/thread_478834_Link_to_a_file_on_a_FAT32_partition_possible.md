---
title: "Link to a file on a FAT32 partition possible?"
date: 2007-06-19
forum: General Help
---

### Post by Howard Kaikow on 2007-06-19
I am trying to create a symbolic link for each of two files on a FAT32 partition.
Error is something like "Operation not perrmitted while creating link to /media/sdf9/..."

I attempted this by right-clicking on the file name and choosing Make Link.

---

### Post by Azakus on 2007-06-19
Is the drive mounted with your user having write-permissions? Try it the command prompt way.
```
sudo ln -s "FILE" "SYMBOLIC LINK NAME"
```

---

### Post by Howard Kaikow on 2007-06-20
> **Azakus said:**
> Is the drive mounted with your user having write-permissions? Try it the command prompt way.
```
sudo ln -s "FILE" "SYMBOLIC LINK NAME"
```

Thanx.
I thought about trying that.
If it works, the GUI needs to be changed to allow the equivalent.

---

