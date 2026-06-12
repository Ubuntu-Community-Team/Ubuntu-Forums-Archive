---
title: "locate files on mounted drive"
date: 2008-04-01
forum: General Help
---

### Post by flennart on 2008-04-01
Hey

Is there a way (terminal) to search for files that are located on a mounted network drive ?
Ive been using 'locate' to search for files that are on my system, but it doesn't seem to work if i have mounted any drives under /mnt. 
The 'locate' command wont look in /mnt even if I use:

# locate file | grep /mnt

thx

/flennart

---

### Post by Arwen on 2008-04-01
I have the same question.
When I type "man locate" it gives a manual of slocate so I think it may be sth like

" slocate -d /media/hdax|grep filename "

but this returns nothing..

---

### Post by cdenley on 2008-04-01
The locate command searches files indexed in a database. The database, by default, does not index any network filesystems, cd/dvd filesystems, or anything in /media since these are usually not persistent, and the database is only updated periodically. You could do something like
```

find /media/mymount -name mysearch

```
Of course, it takes longer to search actual directory listings than it does a database.

---

### Post by Arwen on 2008-04-01
It works for me.Thank you!

---

