---
title: "PostgreSQL 8?"
date: 2005-09-16
forum: General Help
---

### Post by arlie on 2005-09-16
I looked at postgres.org for update but all I can find are fedora and redhat distros. Where can I download postgres 8 for debian?

Please help...

---

### Post by josir on 2005-09-16
Hi arlie, did you find any ubuntu package to run Postgre 8?

Josir Gomes

---

### Post by arlie on 2005-09-16
[QUOTE=josir]Hi arlie, did you find any ubuntu package to run Postgre 8?

Josir Gomes[/QUOTE]
 There is a postgres package but an older version -- postgres 7.

---

### Post by roby1483 on 2005-09-19
Hi,
 I am new of this forum and of Ubuntu.
Still no news of PostgreSQL8 for Ubuntu?

Sorry for my English ;-)

---

### Post by arlie on 2005-09-19
[QUOTE=roby1483]Hi,
 I am new of this forum and of Ubuntu.
Still no news of PostgreSQL8 for Ubuntu?

Sorry for my English ;-)[/QUOTE]
 I found this post on PostgreSQL 8

[http://ubuntuforums.org/showthread.php?t=63986&highlight=postgresql](http://ubuntuforums.org/showthread.php?t=63986&highlight=postgresql)

they seem to be successful in installing PostgreSQL 8 but there using Breezy Badger. Do I need to install Breezy Badger to get an updated PostgreSQL? I'll be installing PosgreSQL 8 to 10 company client branches and I prefer to use Ubuntu instead of Windows.

I'm not sure if my postgres 7 is running. In the System Monitor I could see two tasks running:

     1. postgres: stats buffer proecess
     2. postgres: stats collector proecess

Are these part of the Postgres database server? Is the server running? I like to try version 7. I have pgadmin III installed. How do I connect to postgres using pgadmin3. What's the default user and password. I was able to conect to Windows PostgreSQL 8 but I cannot connect to the one installed on my pc with ubuntu.

When I try to connect I get this error message:

An error has occured:

Error connecting to the server: FATAL:  no pg_hba.conf entry for host "192.168.1.7", user "postgres", database "template1", SSL off

---

### Post by roby1483 on 2005-09-20
[QUOTE=arlie]I found this post on PostgreSQL 8
I'm not sure if my postgres 7 is running. In the System Monitor I could see two tasks running:

     1. postgres: stats buffer proecess
     2. postgres: stats collector proecess

Are these part of the Postgres database server? Is the server running? I like to try version 7.
[/QUOTE]
Try whit "psql <db name>" to see if server is running.
[QUOTE=arlie]
I have pgadmin III installed. How do I connect to postgres using pgadmin3. What's the default user and password. I was able to conect to Windows PostgreSQL 8 but I cannot connect to the one installed on my pc with ubuntu.

When I try to connect I get this error message:

An error has occured:

Error connecting to the server: FATAL:  no pg_hba.conf entry for host "192.168.1.7", user "postgres", database "template1", SSL off[/QUOTE]
The default user is postgres. This error should be resolved if you edit the pg_hba.conf file. If you make a search in the forum or on google you should find more details.

---

### Post by arlie on 2005-09-20
[QUOTE=roby1483]Try whit "psql <db name>" to see if server is running.
[/QUOTE]

What <db name> should I use. Is there a sample database? what is the password for default postgres user?

---

### Post by roby1483 on 2005-09-21
[QUOTE=arlie]What <db name> should I use. Is there a sample database? what is the password for default postgres user?[/QUOTE]
Try with "template1" or with "createdb <db name>" for see if server is runnig. But for use createdb command you must be postgres user.
I don't know the default password for postgres user, you have tried with nothing?
I have installed postgres 8 from the source code and I have create postgres user manually.
For more details [this is the reference documentation](http://www.postgresql.org/docs/8.0/interactive/index.html), the chapter 16 can be much profit for you.
The first time that you use postgres you must lanch the command "initdb" but you find all details on documentation.
I hope to have helped you and to have written in comprehensible mode. If you have more questions don't hesitate to ask.

Roberto.

---

### Post by bernardfrancois on 2005-10-05
[QUOTE=roby1483]for use createdb command you must be postgres user[/QUOTE]
Here it works when I'm not logged in as postgres user...

While reading the manual and installing PostgreSQL8.04, I wrote down the steps I took in my mother tongue (Dutch), just in case if I have to re-install it. I attached the file, and also a file with some commands that where useful for me while using PostgreSQL.

If somebody has troubles installing PostgreSQL and wants to see a translated version of the file, just request it here.

---

### Post by metaele on 2005-10-06
[QUOTE=bernardfrancois]Here it works when I'm not logged in as postgres user...
While reading the manual and installing PostgreSQL8.04, I wrote down the steps I took in my mother tongue (Dutch), just in case if I have to re-install it. I attached the file, and also a file with some commands that where useful for me while using PostgreSQL.
If somebody has troubles installing PostgreSQL and wants to see a translated version of the file, just request it here.[/QUOTE]

Please i would love an english version.

---

### Post by bernardfrancois on 2005-10-09
Here the versions in English.

If you have any questions, or you want to write additional information in those files, you can post here. In the near future, the files will be put on my website (so other people surfing around can also find it).

If anyone wants to build an archive for the universe repository, please do so and contact the person maintaining it (which can be found by a little googling). PostgreSQL is not in the universe, so the version you can get trough synaptic (using the official repository) is not up-to-date at all.

Or if anyone can tell me how to build an archive for the universe repository, then I can do it as well...

---

