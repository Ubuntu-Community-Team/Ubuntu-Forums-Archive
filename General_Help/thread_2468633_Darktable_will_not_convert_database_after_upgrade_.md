---
title: "Darktable will not convert database after upgrade to 3.6.1"
date: 2021-11-06
forum: General Help
---

### Post by cscj01 on 2021-11-06
I have Ubuntu 20.04 x64, and I use the darktable ppa ubuntuhandbook1/darktable.  After the latest update to 3.6.1, when I start darktabke, I get a block that says the following:

> the database schema has to be upgraded for

/home/butch/.config/darktable/library.db

this might take a long time in case of a large database

do you want to proceed or quit now to do a backup

There are two options: (1) close darktable (2) upgrade database

I choose option 2 and nothing happens.

When I run the command to start darktable in a terminal, I get the same block with the 2 choices.  Choosing "upgrade database", I get the following:

```
/usr/bin/darktable %U
[init] can't drop table images_old
[init]   FOREIGN KEY constraint failed
[init] database `library.db' couldn't be upgraded from version 32 to 34. aborting
ERROR : cannot open database
```

I have never done anything to the database other than to use darktable.  Can someone tell me what is going on here (I understand foreign key constraints, but , as I said earlier, I have never modified the database manually ) and how to fix this so I can use darktable again?

---

### Post by monkeybrain20122 on 2021-11-06
I think that mean deleting the old database (/home/butch/.config/darktable/library.db)  and let it generate a new one.

---

### Post by ActionParsnip on 2021-11-06
You may want to contact the PPA maintainer.

---

### Post by cscj01 on 2021-11-06
> **monkeybrain20122 said:**
> I think that mean deleting the old database (/home/butch/.config/darktable/library.db)  and let it generate a new one.After getting assistance from the darktable user list, it seems that all suggestions to find out what may be wrong have yielded no results.  I am just waiting now to find out if there are any others before I go through the arduous task of deleting library.db and re-importing all my images.

---

### Post by cscj01 on 2021-11-06
So I had my xmp files along with my images, so I renamed my library.db to library,backup.db and imported all my directories.  Things are working again.  Although I have no idea why things failed, and there was never a table named images_old in my old library.db, things are working now.  So I'll close this thread even though I would like to know what the developers have to say about this issue.  On the other hand, I'll leave it open for a while to see if I get any information from the developers.

---

