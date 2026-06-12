---
title: "Ubuntu 6.06 Dapper Server Postgres 8.1 Admin Pack for PGAdmin3"
date: 2008-03-17
forum: General Help
---

### Post by Yun_Pilgrim on 2008-03-17
**Problem Installing the Admin Pack**

In my mission to get the admin pack installed, in order to fully use pgAdmin, it has been an uphill struggle, and I need some help.

The admin pack according to [this release note]("https://launchpad.net/ubuntu/+source/postgresql-8.1/") should have been included with version 8.1.4-3, and I am running the latest current version, 8.1.11. 

So far I did the following:

[LIST=1] 
[*]Downloaded the source of the PostgreSQL 8.1.11
[*]Unzipped, and ran ```
 sudo ./confgure =without-readline
```
[*]Extracted the "admin81" directory from [here]("http://developer.pgadmin.org/ftp/release/v1.6.0/adminpacks/admin81-1.6.0.tar.gz") into the ./contrib directory
[*]Ran "sudo make" and "sudo make install"
[*]So far so good, it makes the admin.sql file
[*]Move that file to the "/usr/share/postgresql/8.1/contrib/admin81" dir.
[*]PROBLEM: When I try to import that file into the db (psql -U postgres postgres < /usr/share/postgresql/8.1/contrib/admin81/admin81.sql) I get the error below:
[/LIST]

> ERROR:  could not access file "$libdir/admin81": No such file or directory

This occurs multiple times. Please help. Thank you.

---

