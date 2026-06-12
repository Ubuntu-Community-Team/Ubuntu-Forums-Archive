---
title: "Shell script help"
date: 2008-06-07
forum: General Help
---

### Post by flashuni on 2008-06-07
I am trying to use ditto to create zip archives of every folder inside of the main folder.

Here is what I am using right now:

ditto -c -k -X --rsrc Zip  Zip.zip

I need to be able to zip multiple folders,but not in one archive in separate zip archives.

It is also important that I use ditto because it is the only way to preserve resource files. Please HELP! 

Thanks, Flashuni :KS

---

### Post by geirha on 2008-06-07
There doesn't appear to be any ditto-commands in the hardy repositories, so chances are there are few who knows what that command is or does. You should add some information about it (link to man-page or something)

And why are you using zip? why not tar.gz or tar.bz2?

Sounds like the commands **find** and **tar** can achieve the same thing.

---

### Post by bingoUV on 2008-06-08
> **flashuni said:**
> It is also important that I use ditto because it is the only way to preserve resource files.

What are resource files?

---

### Post by koenn on 2008-06-08
something like this
```
for ITEM in list_of_directories; do
  ditto $ITEM $ITEM.zip
done
```

I assume you're using Mac ?

---

