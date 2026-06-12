---
title: "archive files .zip /stored without compression"
date: 2014-10-21
forum: General Help
---

### Post by shanti2 on 2014-10-21
I tried to compress a folder using archive manager but the zip file has exactly the same size as the original, it just creates an archive no compression, in fact there's no options for the compression rate or anything just file types. Why is archive manager so limited? It has no options,preferences or anything like that! If I try using the command line terminal goes crazy (loads of commmand lines running down) and eventually crashes/freezes the computer. I can't believe I'm spending hours on a task that should take 2 mins!!! Anyone encountered this problem?

---

### Post by sotiris2 on 2014-10-21
What type of files are you trying to archive?

---

### Post by Mark Phelps on 2014-10-21
> I tried to compress a folder using archive manager 

A "folder" has no real size -- it's just a series of pointers to files.  What you have to compress are the actual files themselves, and (pursuent to sotiris2's question) some files can't be compressed hardly at all.

---

### Post by mcduck on 2014-10-21
> **Mark Phelps said:**
> some files can't be compressed hardly at all.

In fact if the original files are already using effective lossy compression methods, trying to compress them into a .zip might actually end creating a file larger than what you had in the first place... :D

---

### Post by andrew.46 on 2014-10-21
As well as considering all of the excellent points above you might consider using *xv *for compression....

---

