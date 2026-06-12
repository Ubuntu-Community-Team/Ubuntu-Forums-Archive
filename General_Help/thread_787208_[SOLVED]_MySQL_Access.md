---
title: "[SOLVED] MySQL Access"
date: 2008-05-08
forum: General Help
---

### Post by ktechman on 2008-05-08
What forum do I need to go to to find out how to access and add to MySql database.

---

### Post by p_quarles on 2008-05-08
What are you using it for? A lot of the most popular MySQL based apps allow you to create a MySQL user that is operated by the app itself, without requiring the human user to do much of anything.

---

### Post by mardawi on 2008-05-08
You can post here
[http://ubuntuforums.org/forumdisplay.php?f=310](http://ubuntuforums.org/forumdisplay.php?f=310)

or check out some MySQL forums

---

### Post by ktechman on 2008-05-08
Have you ever heard of Lyricue?

---

### Post by ktechman on 2008-05-08
I looked in that forum category but didn't see anything that applied. I'll try there thank you.

---

### Post by p_quarles on 2008-05-08
> **ktechman said:**
> I looked in that forum category but didn't see anything that applied. I'll try there thank you.
Please don't create multiple posts on the same topic. It's against the rules here.

---

### Post by ktechman on 2008-05-08
Sorry.  Just answering your question. Lyricue uses MySql as a database.

---

### Post by p_quarles on 2008-05-08
I looked at the documentation page for Lyricue, and it doesn't appear to rely on MySQL. What is it that you are trying to do with it?

---

### Post by ktechman on 2008-05-08
I thought it used MySql to store the songs database. It installed MySql 5 I think, I look at the depends.... When I load lyricue MySql asks for my username and password. I would like to import another database into the present one.

---

### Post by Monicker on 2008-05-08
From looking at these links, it appears that it may indeed rely on mysql.

[http://ubuntuforums.org/showthread.php?t=553078]("http://ubuntuforums.org/showthread.php?t=553078")

[http://packages.ubuntu.com/gutsy/all/lyricue/filelist]("http://packages.ubuntu.com/gutsy/all/lyricue/filelist")

ktechman - Have you installed mysql yet?

---

### Post by ktechman on 2008-05-08
Yes. Lyricue interrupts the install to install it, and asks you to create your username and password. Lyricue comes up and has a basic data base but there is no reference to update the database except adding a song, I have about 120 maybe even more.

---

### Post by Monicker on 2008-05-08
Well, if the databases is there, and you entered the proper credentials to connect, it should work.  I have never used the application myself.  It should have come with some documentation.

---

### Post by ktechman on 2008-05-08
I have scanned the docs but there is no reference to database access. Do you know how to access a MySql database with the command line?

---

### Post by Monicker on 2008-05-08
> **ktechman said:**
> I have scanned the docs but there is no reference to database access. Do you know how to access a MySql database with the command line?

Yes.

```
mysql -u username -p
```


then enter the password when prompted.  

Without understanding how the application interacts with the database, there is good chance you could break something if you manually alter the tables.

---

### Post by ktechman on 2008-05-08
One last question, is there a MySql program with a GUI that will walk me through the admin process or lead me into the right direction?

---

### Post by Monicker on 2008-05-08
There are a couple of gui tools which you can install - Mysql query browswer and Mysql Administrator.  Both will let you see the databases and tables, but the query browser is the tool to use for manual queries against the database.  They are both available in Synaptic.

---

### Post by ktechman on 2008-05-08
Thanks again, I apprecieate your help
             
                      Regards

---

