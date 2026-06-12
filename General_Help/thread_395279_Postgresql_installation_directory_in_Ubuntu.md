---
title: "Postgresql installation directory in Ubuntu?"
date: 2007-03-27
forum: General Help
---

### Post by newtonviet on 2007-03-27
I am installing a software in Ubuntu 6.10 that required the PostgreSQL database server. I have installed the server 8.1 by apt-get and now the Postgresql server is running.

However, the software wizard asks for the Installation Directory of Postgresql. "Please specify the directory where the binaries of your PostgreSQL installation are located".

After trying to find it in the File system, I could only found 2 folders in usr/share:

postgresql/8.1/
postgresql-common/

and put it in the installation directory box,  but the wizard refuses and the error is:
"the directory usr/share/postgresql/8.1/ does not seem to contain a psql executable."

Could somebody tell me where to find the location of that  psql executable? Thanks.

---

### Post by useResa on 2007-03-28
> **newtonviet said:**
> I am installing a software in Ubuntu 6.10 that required the PostgreSQL database server. I have installed the server 8.1 by apt-get and now the Postgresql server is running.

However, the software wizard asks for the Installation Directory of Postgresql. "Please specify the directory where the binaries of your PostgreSQL installation are located".

After trying to find it in the File system, I could only found 2 folders in usr/share:

postgresql/8.1/
postgresql-common/

and put it in the installation directory box,  but the wizard refuses and the error is:
"the directory usr/share/postgresql/8.1/ does not seem to contain a psql executable."

Could somebody tell me where to find the location of that  psql executable? Thanks.

I have postgresql 8.2 installed and am not sure if the file locations are identical or not.
Therefore let me try to explain how I searched for the executable.
In a terminal first issue the command
```
sudo updatedb
```Please note this may take some time
Next issue the command
```
locate psql
```You will get a list of locations where the word **psql** is found

In my case the result was
> rdrijsen@rdrijsen-laptop:~$ locate psql
/var/lib/dpkg/alternatives/psql.1.gz
/var/lib/postgresql/.psql_history
/etc/alternatives/psql.1.gz
/usr/bin/psql
**/usr/lib/postgresql/8.2/bin/psql**
/usr/lib/odbc/libodbcpsqlS.so
/usr/share/doc/postgresql-doc-8.2/html/app-psql.html
/usr/share/locale-langpack/en_GB/LC_MESSAGES/psql-8.1.mo
/usr/share/man/man1/psql.1.gz
/usr/share/postgresql/8.2/man/man1/psql.1.gz
/usr/share/postgresql/8.2/psqlrc.sample
/usr/share/pgadmin3/docs/en_US/pg/app-psql.htmlThe line in bold indicates the location of the executable of the installation.
Most of the time executables can be found in a **bin** directory.

Hope this will help you to find the executable

---

### Post by newtonviet on 2007-03-29
It works. Thank you!

---

### Post by useResa on 2007-03-29
> **newtonviet said:**
> It works. Thank you!
Glad that you have been able to solve this.
No problem, glad to I could help you out.

---

