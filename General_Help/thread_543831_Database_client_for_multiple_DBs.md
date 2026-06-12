---
title: "Database client for multiple DBs"
date: 2007-09-05
forum: General Help
---

### Post by Jamie Jackson on 2007-09-05
I'm looking for a Free DB client. I use mysql, mssql, and oracle. I also have Eclipse, so there might be a plugin option, but when I looked at Eclipse options before, I got very confused.

Any tips would be appreciated.

---

### Post by Jamie Jackson on 2007-09-17
I found (and am using) squirrel, but am wondering if there's another (better) on that I missed.

---

### Post by pjkoczan on 2007-09-17
There are a number of other database-independent clients available, like DBI for Perl, DB-API for Python,  JDBC for Java, PHP's own database connectivity interface, and ODBC for most everything else. Keep in mind that you will have to download appropriate drivers for your DB systems (i.e. for squirrel you'll need JDBC drivers for MySQL, MSSQL, and Oracle, otherwise it won't work).

As an aside, I couldn't really find any independent interface that's a GUI or shell like squirrel appears to be, mostly functions that you use within another programming language. What you want depends mostly on whether or not you just want a program to manage all your databases or if you want to write your own database-driven programs.

---

### Post by Jamie Jackson on 2007-09-17
I use JDBC for programming, but in this case I'm talking about a GUI DB client (like Squirrel, which I'm currently using against both Oracle and MSSQL).

If anybody's got any alternate GUI DB client suggestions, let me know...

---

