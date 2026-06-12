---
title: "using updatedb"
date: 2007-02-26
forum: General Help
---

### Post by balan on 2007-02-26
Hope someone can help. 

If I run "sudo updatedb", it only indexes the root drive, how do I make it index all the hard drives on my computer?

Al

---

### Post by scxtt on 2007-02-26
check out  /etc/updatedb.conf ... looks like by default it doesn't index anything in /media, so anything mounted there isn't indexed - and the whole /media scheme is default in *buntu ...

---

### Post by balan on 2007-02-26
Wow!! Thanks a million.

Just removed the "/media" from the PRUNEPATHS & now it works perfectly.

Al

---

### Post by plinydogg on 2007-11-01
Just to clarify for anyone else reading this thread: after removing "/media" from the PRUNEPATHS variable in /etc/updatedb.conf and saving it, you have to run updatedb again.

---

