---
title: "Amarok: MySQL vs SQLlite"
date: 2008-05-06
forum: General Help
---

### Post by intense.ego on 2008-05-06
What's the difference between these two? I understand MySQL is supposed to be faster, but what is the disadvantage? If there wasn't any, why wouldn't it be  the automatic default in Amarok?

---

### Post by wdaniels on 2008-05-06
> **intense.ego said:**
> MySQL is supposed to be faster, but what is the disadvantage? If there wasn't any, why wouldn't it be  the automatic default in Amarok?

MySQL is a much heavier dependency to create for no clear need. It's unlikely that anybody would really need the higher performance of MySQL just for their music catalog, but it might make sense in some cases; maybe if you're already using MySQL for stuff on your desktop, or if you want to share a single catalogue between multiple systems a MySQL database could possibly be a more elegant way to do that.

The only point about the two methods that I can think to note is that whilst the SQLlite file will be created in your home directory, a MySQL database will not (or at least not by default), so you have to remember that if you re-install parts of your system expecting all the user data to be kept safe in the home partition.

---

### Post by hyper_ch on 2008-05-06
I'd say if you have sever thousand music files and lyrics and artwork and and and and then mysql will outperform sqlite for indexing, searching etc. but I haven't really measured it.

---

### Post by intense.ego on 2008-05-06
I have a 30,000 song music collection played off an external hard drive. It surely would help in my case, right? Amarok is sluggish when it comes to searching/indexing songs (with SQLlite right now) and it was considerably worse before I upgraded my RAM.

---

### Post by p_quarles on 2008-05-06
Historically, many of the indexing problems that people experience with Amarok (including freezes/crashes) are solved by MySQL. Yes, it's a heavier server, but it's also just more reliable. 

A how-to:
[http://amarok.kde.org/wiki/MySQL_HowTo](http://amarok.kde.org/wiki/MySQL_HowTo)

---

### Post by Steveway on 2008-05-06
Just to keep things eval. You should also try PostgreSQL.
Many people experience even faster performance with PostgreSQL than with MySQL, besides that I didn't see any real benchmarks.
But since I used both (Now only PostgreSQL) I would say that PosgreSQL feels subjectively faster.
You should try both (especially for the learning-effect) and see which you prefer.

---

### Post by p_quarles on 2008-05-06
> **Steveway said:**
> Just to keep things eval. You should also try PostgreSQL.
+1

Whether it's faster or not, the future of MySQL now seems to be rather uncertain, after its acquisition by Sun. The wiki page I linked to also includes instructions for PostgreSQL.

---

### Post by Monicker on 2008-05-06
> **intense.ego said:**
> I have a 30,000 song music collection played off an external hard drive. It surely would help in my case, right? Amarok is sluggish when it comes to searching/indexing songs (with SQLlite right now) and it was considerably worse before I upgraded my RAM.

I would say go with mysql.  My music collection was less than half of yours when I first started using Amarok, and sqlite constantly caused problems for me.  Its been running smooth since I switched to mysql.

---

### Post by wdaniels on 2008-05-06
> **intense.ego said:**
> I have a 30,000 song music collection played off an external hard drive. It surely would help in my case, right? Amarok is sluggish when it comes to searching/indexing songs (with SQLlite right now) and it was considerably worse before I upgraded my RAM.

If you find it sluggish with SQLlite then certainly I would switch. I only have around 2,500 songs so I never noticed any problem myself. I'm a little surprised that even 30,000 should be any kind of challenge even for SQLlite, but if there's some history of other sorts of problems too...

There's no "disadvantage" to a heavier RDBMS other than being a more complex dependency, hence the reason it's not the case by default.

Personally, I would choose PostgreSQL over MySQL, all else being equal.

---

### Post by 7x1x on 2009-10-11
I've tried SQLite and MySQL and did a couple of tests nothing fancy.
My collection is 4675 files (25.2 GB) on an ntfs partition.

Time to rescan:
MySQL 3:22
SQLite 6:48

Load a smart playlist 4485 songs:
MySQL 4.62
SQLite 2.82

Time to start with 4485 songs:
MySQL 9.41
SQLite 6.60

---

