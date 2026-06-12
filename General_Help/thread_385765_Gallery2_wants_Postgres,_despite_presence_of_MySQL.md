---
title: "Gallery2 wants Postgres, despite presence of MySQL"
date: 2007-03-16
forum: General Help
---

### Post by Explodinglemur on 2007-03-16
I seem to have a bit of a dependencies problem on an Edgy server.  I have the packages mysql-server, mysql-client, and mysql-common installed.  When I attempt to install gallery2, aptitude tries to install postgresql as well.  In the dependencies list for gallery2, it has this under recommendations:
mysql-server-4.1 | mysql-server, postgresql-7.4 | postgresql-8.0

That seems to indicate it depends on both (mysql-server-4.1 OR mysql-server) AND (postgresql-7.4 OR postgresql-8.0)

Why would it require some version of both MySQL and Postgresql?  Perhaps I'm missing something.  In any case, I'd like to be able to install it without aptitude attempting to install Postgresql as well.  Thanks!

---

### Post by rmsx99 on 2007-05-18
I'm having this problem as well.

How does one omit a package (in this case, postgresql) from an aptitude install?

The requirements for Gallery2 are MySQL *or* PostgreSQL, so I find it a waste that it's trying to install the latter.

---

