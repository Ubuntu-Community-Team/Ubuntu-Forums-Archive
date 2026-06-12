---
title: "[SOLVED] how do I make a diff between the contents of two directories?"
date: 2008-01-05
forum: General Help
---

### Post by delfick on 2008-01-05
hello

I have one folder full of folders, all full of files

and a copy of that folder with the same folders and files inside, except I've added some things to some of the files.

How would I produce a .patch file with all those changes in it ?? :D

thnx

---

### Post by lloyd_b on 2008-01-05
> **delfick said:**
> hello

I have one folder full of folders, all full of files

and a copy of that folder with the same folders and files inside, except I've added some things to some of the files.

How would I produce a .patch file with all those changes in it ?? :D

thnx

Try this: ```
 diff -r folder1 folder2 
```
The "-r" means "recursive" - it scans all files in the specified directory (folder1), and all files in subdirectories beneath it, and compares them to the corresponding files in the second directory (folder2).

Lloyd B.

---

### Post by delfick on 2008-01-05
cool

I knew it'd be something simple :D

the next question becomes what command to patch the original folder with the resulting patch file from

diff -r ./Original ./Final > thePatch.patch

?? :D

thnx

---

### Post by shirilover on 2008-01-05
That would be
patch -p0 < thePatch.patch

---

### Post by delfick on 2008-01-05
hmm, wrong p option

> (Stripping trailing CRs from patch.)
can't find file to patch at input line 2
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -r Original/FP8/XMLNode.as Final/FP8/XMLNode.as
--------------------------
File to patch: 

...

---

### Post by delfick on 2008-01-05
don't worry about it :D

I followed this page here [http://www.cpqlinux.com/patch.html](http://www.cpqlinux.com/patch.html)

and used diff -Naur olddir newdir > new-patch

and now 

patch -p0 < patch.patch works 

thnx peoples :D

---

