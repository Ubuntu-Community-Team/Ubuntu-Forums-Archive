---
title: "MS SQL tool?"
date: 2008-06-25
forum: General Help
---

### Post by jimv on 2008-06-25
Is anyone aware of any program that will allow one to run queries, make tables, etc on Microsoft SQL Server 2005?

Something similar to MS SQL Server Management Studio would rock my socks.

---

### Post by jimv on 2008-06-26
Burp

---

### Post by jonabyte on 2008-06-26
do you mean from your ubuntu desktop? I don't believe there are any programs, oss anyways for that.
You can try to rdp into the server.

---

### Post by Nepherte on 2008-06-26
these two should do just fine:
```
sudo apt-get install mysql-admin mysql-query-browser
```

---

### Post by oxsyn on 2008-07-14
sqsh is a command line utility for MS SQL.  I haven't used it yet, will be later today though.

> commandline SQL client for MS SQL and Sybase servers
sqsh is a flexible commandline utility that uses the freetds libraries
to connect to Sybase or Microsoft SQL servers.  It is a useful debugging
tool for identifying problems with other SQL applications, and it can be
used as a productivity tool in its own right:  unlike most SQL CLIs, sqsh's
interactive shell lets you pipe the output of SQL queries directly to other
Unix commands for further processing.

---

### Post by nu2 on 2009-02-27
> sudo apt-get freetds unixodbc

but i'm still at lost configuring it. need some help!

---

