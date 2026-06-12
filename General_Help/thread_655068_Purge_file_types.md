---
title: "Purge file types"
date: 2007-12-31
forum: General Help
---

### Post by rkillcrazy on 2007-12-31
I am in the process of moving into Ubuntu from Vista.  :lolflag:  (I still laugh at that statement as I'm an MS network admin by trade.)  I have a large music collection that I generated over the years of using Windows.  I have each artist in their own directory and then separated further via albums.  I have the MP3s and a folder.jpg in each of the album folders.  However, here's my issue...  I also see **desktop.ini** and **thumbs.db** in those folders as well.  I wish to have a script, or something of the sort, go through and dig that stuff out of 10GB of music.  Any ideas?  If need be, I can try to do something similar with FOR statements in Windows I suppose.  However, FOR statements are almost as foreign to me as Ubuntu's command line.

12-31-07
2131 EST

---

### Post by shad0w_walker on 2007-12-31
You can use find to manage this. Open up a terminal (Applications > Accessories > Terminal) and use the cd command to change to your music folder. Then run this command:

```
find ./ -name thumbs.db -delete
```

This will search through all the subfolders from the current folder downwards and delete any files it finds called thumbs.db. To get rid of any other files just change the name you are looking for.

---

### Post by rkillcrazy on 2007-12-31
> **shad0w_walker said:**
> You can use find to manage this. Open up a terminal (Applications > Accessories > Terminal) and use the cd command to change to your music folder. Then run this command:

```
find ./ -name thumbs.db -delete
```

This will search through all the subfolders from the current folder downwards and delete any files it finds called thumbs.db. To get rid of any other files just change the name you are looking for.

SWEET!  :guitar:

That worked like a charm.  Thanks, man!

For anyone else who comes across this, it's case sensitive.  I did the string with **thumbs.db** and ran it again with **Thumbs.db**.

---

### Post by dlegend on 2007-12-31
> **rkillcrazy said:**
> SWEET!  :guitar:

That worked like a charm.  Thanks, man!

For anyone else who comes across this, it's case sensitive.  I did the string with **thumbs.db** and ran it again with **Thumbs.db**.

In Linux, everything is case sensitive. You can have two files with the same name as long as the case is different. Just as in many programming languages you can have variables with the same name as long as casing is different =)

---

### Post by ghostdog74 on 2007-12-31
> **rkillcrazy said:**
> 
For anyone else who comes across this, it's case sensitive.  I did the string with **thumbs.db** and ran it again with **Thumbs.db**.
```

find ./ -name [Tt]humbs.db -delete

```

---

### Post by nick_h on 2008-01-01
If you don't want it case sensitive you can use -iname instead of -name in the *find* command.

---

### Post by rkillcrazy on 2008-01-01
> **nick_h said:**
> If you don't want it case sensitive you can use -iname instead of -name in the *find* command.

Yeah, I tested the following string on another folder I had full of unwanted files and it worked fine - regardless of the spelling.

```

find ./ -iname thumbs.db -delete

```

---

