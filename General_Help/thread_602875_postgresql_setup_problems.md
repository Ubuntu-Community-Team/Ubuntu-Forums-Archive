---
title: "postgresql setup problems"
date: 2007-11-04
forum: General Help
---

### Post by DagonX on 2007-11-04
I followed the instruction in [https://help.ubuntu.com/community/PostgreSQ](https://help.ubuntu.com/community/PostgreSQ) and executed the following  commands:

sudo -u postgres createuser -D -A -P myuser
sudo -u postgres createdb -O myuser mydb

When I attempted to access the database I received the following error:

dagon@DagonUX32:~$ psql mydb
psql: FATAL:  role "dagon" does not exist.

There was an excellent post about this subject. When I tried the method in the post I get the following error:

dagon@DagonUX32:~$ sudo psql COREJAVA
psql: FATAL:  role "root" does not exist


What is the key to making Postgresql work?

Charles

---

### Post by osnewbie on 2008-05-29
if you go here
[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)
you have to first edit /etc/postgresql/8.1/main/pg_hba.conf

---

