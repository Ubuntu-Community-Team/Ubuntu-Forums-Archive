---
title: "Lost movies"
date: 2015-01-17
forum: General Help
---

### Post by cowboy7305 on 2015-01-17
I had a lot of movies in the download folder and i thought i would clean the folder up a bit so i made a folder in the download folder called Movies and started to cut and paste some of the movies over, all went well or so i thought
i have just looked in this new folder no movies in it ,so i have lost them,
OR HAVE I
is there a way to find them after cutting and pasting 
thanks

---

### Post by tgalati4 on 2015-01-17
*photorec* will probably recover the files.  It is installed with *testdisk*.  I find it difficult to believe that cut and paste failed.  The files are not deleted until they are successfully moved to the new location.  Perhaps your disk is having problems.

Open a terminal:

```
dmesg | tail -40
```

Look for disk drive read or write errors.

---

### Post by nerdtron on 2015-01-18
did your disk usage shrink after you have cut and paste them? if not, then you probably have pasted them on another location.

Just use the find tool if you remember some filenames and you should see where you pasted them.

---

### Post by mooreted on 2015-01-18
I tested photorec the other day. I had a thumbdrive that had the partition deleted, a new partition added and formatted. Photorec still recovered all the files. Pretty amazing.

---

