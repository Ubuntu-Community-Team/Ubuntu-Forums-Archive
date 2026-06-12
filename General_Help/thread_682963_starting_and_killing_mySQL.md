---
title: "starting and killing mySQL"
date: 2008-01-30
forum: General Help
---

### Post by nanogeek on 2008-01-30
I am having a little newbie problem here.
I installed LAMPP on my machine and all was well.
I then installed a MySQL client so I could experiment with databases.
Now when I boot my machine it appears that MySQL sets itself up to run automagically and when I want to start LAMPP I get an error message that MySQL is already running. To get LAMMPP to start properly I need to:
kill mysql daemon

/etc/init.d/mysql stop


and then  start lammp
/opt/lampp/lampp start

How do I prevent the mysql daemon from starting itself at boot?
How do I get lammp to start at boot?

TIA
nanogeek

---

### Post by ayoli on 2008-01-30
> **nanogeek said:**
> I am having a little newbie problem here.
I installed LAMPP on my machine and all was well.
I then installed a MySQL client so I could experiment with databases.
Now when I boot my machine it appears that MySQL sets itself up to run automagically and when I want to start LAMPP I get an error message that MySQL is already running. To get LAMMPP to start properly I need to:
kill mysql daemon

/etc/init.d/mysql stop


and then  start lammp
/opt/lampp/lampp start

How do I prevent the mysql daemon from starting itself at boot?
How do I get lammp to start at boot?

TIA
nanogeek

a quick fix to your problem could be:
```
sudo chmod a-x /etc/init.d/mysqld
```
this disable the exec of the mysqld start/stop script
then :
```
sudo ln -sf /opt/lampp/lampp /etc/init.d/
```
make sure these 2 are executables.

btw, there must have a better method with *update-rc.d* (there is a man page I think)

I do not use LAMPP, I've installed my lam stack (almost) like this : [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

edit: I guess the mysql client package you have installled has come with the server (from ubuntu repository , so you have 2 mysql install; ubuntu one and lampp one, and that's why you have a mysqld in init.d now, IMO, it is more flexible to work with a lamp stack as described in the wiki (link above)

---

### Post by eggdeng on 2008-01-30
```
sudo apt-get install bum
```
Screenshot attached.

---

### Post by monkey56657 on 2008-01-30
System -> Preferences -> Session 

The first tab is "Startup Programs"

However it doesn't list all the programs that something such as BUM as posted above would do so may or may not be useful.

---

### Post by nanogeek on 2008-01-30
System -> Preferences -> Sessions
does not show mySQL or LAMMP or any of its components
Will BUM?

---

### Post by ayoli on 2008-01-30
bum groups "System -> Preferences -> Session -> Startup Programs" and "System -> Administration -> Services" I think.
But I keep my opinion that installing a lamp stack based on ubuntu packages is better (security upgrades, reliability, ...)

---

### Post by nanogeek on 2008-01-30
OK
I was able to stop mySQL from loading at boot by using BUM

BUM shows mySQL three times.
once as "Fast and Stable SQL Database Server <br> mysql"
And twice as "mySQL binaries"
I unchecked them all
(BTW the binaries listings disappeared from the list of programs in BUM, how can I restore them in the future if need be?)

Now how do I get LAMPP to start at boot?

---

### Post by ayoli on 2008-01-30
> **nanogeek said:**
> OK
I was able to stop mySQL from loading at boot by using BUM

BUM shows mySQL three times.
once as "Fast and Stable SQL Database Server <br> mysql"
And twice as "mySQL binaries"
I unchecked them all
(BTW the binaries listings disappeared from the list of programs in BUM, how can I restore them in the future if need be?)

Now how do I get LAMPP to start at boot?

you may want to read my first answer.
Now you have bum you could also add /opt/lampp/lampp script to startup scripts.

---

