---
title: "folder tree copying with rsync"
date: 2008-04-13
forum: General Help
---

### Post by geo909 on 2008-04-13
Hello everybody,
I would like to backup the subfolders structure of a folder.
That is, backup the (only first level of) subfolders without their contents..

I think I have done this once, using rsync but I can't find out how I did it..
Any ideas, please?


Thanks!

---

### Post by ajgreeny on 2008-04-13
I think, but I'm not sure it's ```
rsync source destination -d
```  You may find it works but as I say I'm not too certain, the **man rsync**, like most man pages, is a bit of a mystery when it comes to the detailed explanations of what the options means in practice.

---

### Post by geo909 on 2008-04-13
Yes, that did the job..
Was too lost in the man page to find out.
Thank a lot!

---

