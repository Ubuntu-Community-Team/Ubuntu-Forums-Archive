---
title: "php5 + Apache2 + POstgreSQL"
date: 2005-04-12
forum: General Help
---

### Post by taluna on 2005-04-12
Hi, 

I installed PHP5(PHP5.0.4) and Apache2(Httpd-2.0.53) from source file (tar.gz) and PostgreSQL with apt-get install.

I have problem when I try to configure compile options to PHP5 to pgsql extension.

*./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-pgsql*

and shows this error (last three lines):

[I]checking for PostgreSQL support... yes
checking for pg_config... not found
configure: error: Cannot find libpq-fe.h. Please specify correct PostgreSQL installation path[/I]

Where is the PostgreSQL installation path ? I need to write this information in pgsql compile option in ./configure command

e.g *./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-pgsql=/usr/local/postgresql*

PS: I've already this location option showed in example and it didn't work

---

### Post by accuser on 2005-04-13
I don't know the specific answer to you question, but you can get a list of files installed by a package using:
```
$ dpkg-query -L postgresql
```
Hope that helps!

---

### Post by taluna on 2005-04-20
Hi, 

this command helped me to list all the pathes where there is some postgresql
configuration, files .. but I can find the real installation path. 

I tried all the options below and none of them worked. 


/var/run/postgresql

/usr/lib/postgresql/bin

/usr/lib/postgresql

/usr/share/postgresql

/etc/init.d/postgresql

/etc/postgresql

The same error appears for all of them:

[I]checking for pg_config... not found
configure: error: Cannot find libpq-fe.h. Please specify correct PostgreSQL installation path
[/I]

I can't compile php5 because I dont know the correct POstgreSQL installation path :(

I dont know if it's necessary default path "/usr/local/postgresql" to compile php5.. I'm following the instructions to define a path if it's not default.

---

### Post by anandkaushik on 2005-04-20
Hi, 

You must install "postgresql-devel-8.0.1-2PGDG.i686.rpm" to install development
and if installed postgresql from RPMS then give path /var/lib/pgsql

and see it works :)

---

