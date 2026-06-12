---
title: "MythTV Help"
date: 2008-03-23
forum: General Help
---

### Post by Scubastev013 on 2008-03-23
Hello,

I'm trying to get MythTV working on 7.10.  Add/Remove installs MythTV frontend and backend fine.  When I click on the front end it tells me that it cannot detect my database.  I have tried entering different information in the boxes, but nothing seems to work.  What can I do?

---

### Post by .nedberg on 2008-03-23
Did you set up the backend? Did you start it? Myth is hard to set up on a working machine like this. I would recommend mythbuntu if you can use that. It makes it easy!

---

### Post by von3kus on 2008-03-23
Hello,

I've had the same problem.. I discovered using phpMyAdmin that there was no MythTv database on my backend.

You can solve this by executing:
(mc.sql is located in /usr/share/mythtv/sql)
```
mysql < mc.sql
``` or query the content of
```
mythtv_x.xx.x.sql
``` (also located in /usr/share/mythtv/sql) in your phpMyAdmin

---

### Post by Scubastev013 on 2008-03-23
How do I execute those lines of code?  I'm semi new at Ubuntu and completely new to programming php.

Would it be easier to just install mythubuntu?

---

### Post by .nedberg on 2008-03-23
It is generally not recommended to keep a Myth backend on the same computer as your main desktop. If you can, I would recommend installing [mythbuntu]("http://mythbuntu.org/")!

I used to use KnoppMyth but switched to mythbuntu in November, I have never regretted that! Mythbuntu is just great!

---

