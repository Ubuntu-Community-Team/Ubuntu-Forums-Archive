---
title: "Db/DBMS advice needed"
date: 2014-03-05
forum: General Help
---

### Post by jwaclawsky on 2014-03-05
I am working with some friends to develop a web site designed to help awareness and focus on sucide prevention for our returning veterns, families and friends. We ware recently touched by this horrible event. We are in the early stages and have a limited budget. We are looking for data base suggestions and advice (actually any experience based suggestions are appreciated including using cloud DB tools etc.). We are still sizing the requirements. But it is difficult at this point to understand what level of web traffic and data base activity that are likely to be generated. Two questions: (1) if this is the correct place to ask this question then can someone recommend a free/inexpensive DB/DBMS that is simple, reliable and scales well (if needed). (2) If this is not the correct place where should I post this question?

---

### Post by SeijiSensei on 2014-03-05
The usual answer is [MySQL]("http://www.mysql.com/"), but I'm going to suggest you use [PostgreSQL]("http://www.postgresql.org/about/") instead.  [This article]("http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL") provides a fairly unbiased comparison of the two.

I've used PostgreSQL as the back end for web sites for nearly two decades.  I have never found it slow.  I have also used it on databases with millions of records.  In that case having the correct indexes makes an enormous difference for performance.

There is a web-based management tool, [phpPgAdmin]("http://phppgadmin.sourceforge.net/doku.php").  You can also install an [ODBC driver]("http://www.postgresql.org/ftp/odbc/versions/") on Windows machines and connect to PG databases from applications like Microsoft Access.

Both of these are freely-distributed, but MySQL is now owned by Oracle, whereas PostgreSQL is a community-supported project.  As the linked comparison observes, "MySQL is an open-source PRODUCT. Postgres is an open-source PROJECT."

---

### Post by bab1 on 2014-03-05
> **SeijiSensei said:**
> ...
Both of these are freely-distributed, but MySQL is now owned by Oracle, whereas PostgreSQL is a community-supported project.  As the linked comparison observes, "MySQL is an open-source PRODUCT. Postgres is an open-source PROJECT."

A drop in replacement for MySQL is [MariaDB]("https://mariadb.org/").  Quoting from their website: > "MariaDB is a drop-in replacement for MySQL.

MariaDB strives to be the logical choice for database professionals looking for a robust, scalable, and reliable SQL server. To accomplish this, the MariaDB Foundation work closely and cooperatively with the larger community of users and developers in the true spirit of Free and open source software, and release software in a manner that balances predictability with reliability."

---

### Post by jwaclawsky on 2014-03-06
Many Thanks for the replies! I will look over the suggestions and carefully read their documentation. I assume I should stay away from Oracle because of cost and being part of Oracle. If anyone else has any advice or suggestions please let me know.

---

