---
title: "What command would I use to move a file from one file to another?"
date: 2007-06-18
forum: General Help
---

### Post by swoll1980 on 2007-06-18
Let me know please.  (I'm sorry one folder to another)

---

### Post by AriciU on 2007-06-18
mv /pathto/folder /pathto/whereuwannamove/folder

---

### Post by yabbadabbadont on 2007-06-18
I assume you mean in a terminal window or on the console.  ;)

The "mv" (move) command is what you need to use.  "man mv" for details on its options, but the short answer is:

mv file /path/to/new/directory
or
mv /path/to/file /path/to/new/directory
or
mv file /path/to/new/directory/newfilename  (you can change the name as you move the file)

The mv command is also used to rename a file or directory:

mv oldfilename newfilename
mv oldDirectoryName newDirectoryName

There are a lot of things you can do with it.  Read the man page for details.

---

### Post by swoll1980 on 2007-06-18
Thank you

---

