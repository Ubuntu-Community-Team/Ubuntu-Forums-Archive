---
title: "Lampp (Xampp) + MythTv = Nasty error"
date: 2007-04-11
forum: General Help
---

### Post by LtPitt on 2007-04-11
Hello there!
I have a nice Lampp installation, working fine, except I don't know how to configure webmin with Lampp paths (everything is installed in /opt/lampp)...
The main problem is that I've tried to install mythtv but I get a sql error (probably because i've tried to install sql server OVER the one that Lampp installed).
When I run Mythtv from terminal I get this:

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-04-11 21:13:25.023 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-04-11 21:13:25.080 Unable to connect to database!
2007-04-11 21:13:25.081 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

When I run apt-get autoremove it says me:

1 non completamente installati o rimossi.
È necessario prendere 0B di archivi.
Dopo l'estrazione, verranno occupati 0B di spazio su disco.
Configuro mysql-server-5.0 (5.0.24a-9ubuntu2) ...
 * Stopping MySQL database server mysqld                                 [ ok ]
chown: impossibile accedere a `/var/run/mysqld': Nessun file o directory
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: errore processando mysql-server-5.0 (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 1
Sono occorsi degli errori processando:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

Forgive me for the Italian copy/past but it should (hopefully) be understandable...
Any hints? :(

---

### Post by superm1 on 2007-04-11
I'd say purge and reinstall mysql-server
```

sudo apt-get remove --purge mysql-server mysql-server-5.0

sudo apt-get install mysql-server
```

---

### Post by LtPitt on 2007-04-11
Does it affect Lampp too? 
I have my whole blog there :(

---

### Post by superm1 on 2007-04-11
Well i can't comment much about lammp, as I've never worked with it.  Did it install its own SQL server into /opt/lammp then I Take it?  Is this sql server running normally?

If so, your only real option is to set the SQL server lammp is using to go on a different port, or install mythtv from source so that you don't need to install mysql-server-5.0

---

### Post by LtPitt on 2007-04-11
It... Just...
WORKED :D

I'm a noob and I love you =)

During uninstall it asked me if I'd like to keep sql data.
SWEET :D

But I'm still not able to run mythtv...

The problem key is here:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/opt/lampp/var/mysql/mysql.sock' (2)


I should be able to use the socked above instead of the default one that you can find in my previous post...
How can I force this?

---

### Post by LtPitt on 2007-04-11
ps

yes, that sql server (in /opt/lampp) is working perfectly

---

### Post by LtPitt on 2007-04-11
I'm suffering so much :(

I keep on uninstalling mysql but it doesn't work...
My adept manager got stuck and I had to

 sudo dpkg --configure -a


Configuro mysql-server-5.0 (5.0.24a-9ubuntu2) ...
 * Stopping MySQL database server mysqld                                 [ ok ]
chown: impossibile accedere a `/var/run/mysqld': Nessun file o directory
 * Starting MySQL database server mysqld                                 [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: errore processando mysql-server-5.0 (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 1
Sono occorsi degli errori processando:
 mysql-server-5.0


No luck :'(

---

