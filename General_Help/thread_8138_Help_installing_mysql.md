---
title: "Help installing mysql"
date: 2004-12-14
forum: General Help
---

### Post by Cstark on 2004-12-14
Hi, i'm trying to install mysql using the RPM package but i get the following error:

root@starky:/home/starky # rpm -i MySQL-server-4.1.7-0.i386.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

Does anyone have a solution for this or maybe another method? i've tried following the instructions from the thread "How To: Setup a Development Webserver" but didn't manage to get the mysql installed that way. :(

I'm pretty new to Linux/Ubuntu so please go easy on me. :)

Thanks.

Crap wrong forum, can a mod move this for me please? Sorry. :(

---

### Post by Johan on 2004-12-14
Are you using Ubuntu? Then you should use the apt-tools instead of rpm. The command would be ```
apt-get install mysql-server
``` if you want the server-package. Try ```
apt-cache search mysql
``` to list all the packages that concern mysql.

---

### Post by Cstark on 2004-12-14
> Are you using Ubuntu?

Yea, soz shoulda made it clear.

Tried using the apt-get install mysql-server but got the following:

```
root@starky:/home/starky # apt-get install mysql-server
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package mysql-server
root@starky:/home/starky #
```

And when using the search, the only one that seemed to be appelling was mysql-common which i got the following:

```
root@starky:/home/starky # apt-get install mysql-common
Reading Package Lists... Done
Building Dependency Tree... Done
mysql-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@starky:/home/starky #

```

Sorry if this is so simple to get working, but im new to this all. :(

---

### Post by jdodson on 2004-12-14
[QUOTE=Cstark]Yea, soz shoulda made it clear.

Tried using the apt-get install mysql-server but got the following:

```
root@starky:/home/starky # apt-get install mysql-server
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package mysql-server
root@starky:/home/starky #
```

And when using the search, the only one that seemed to be appelling was mysql-common which i got the following:

```
root@starky:/home/starky # apt-get install mysql-common
Reading Package Lists... Done
Building Dependency Tree... Done
mysql-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@starky:/home/starky #

```

Sorry if this is so simple to get working, but im new to this all. :([/QUOTE]

 
type this into the console:

```
sudo synaptic
``` 

then search for mysql, make sure you have the server selected, click apply.

if you still cannot do it check the following documentation:

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

