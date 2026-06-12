---
title: "[SOLVED] SQLite database browser"
date: 2008-07-09
forum: General Help
---

### Post by cpetercarter on 2008-07-09
I have an application on my computer which has generated a SQLite2 database. I want to use the SQLite database browser to check the database to see that the application is running as it should. But the browser will not open the database, and returns an error message that the file is not an SQLite 3 database. I am sure that the SQLite database browser will in fact open a SQLite2 database. What do I have to do to make it open this one?

---

### Post by cpetercarter on 2008-07-09
OK, I've found the answer. It appears that the latest version of the SQLite database browser will open only sqlite3 databases. If you want to open an sqlite2 database, you need version 1.1 of the browser. And no-one knows where to find it. So I will just have to use the cli.

---

### Post by Delistone on 2010-02-13
I ran into this too and the above post helped me.
I'll just add that you *can* find version 1.1 on Sourceforge.

[http://sourceforge.net/projects/sqlitebrowser/files/](http://sourceforge.net/projects/sqlitebrowser/files/)

Cheers!

---

### Post by PePas on 2013-04-18
Yes, versions 1.1 works for sqlite2 files. I needed to install libqt3-mt from precise and libstdc++5 (from my regular quantal).

---

### Post by papibe on 2013-04-18
Please don't reply on old threads. It is much better to create a new one. Feel free to link this one if you want.

From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

**Thread Closed**.

---

