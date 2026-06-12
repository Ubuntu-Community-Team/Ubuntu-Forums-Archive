---
title: "error binding values with 3.1.11 connector/j to server-side prepared statements on my"
date: 2005-10-18
forum: General Help
---

### Post by mpo on 2005-10-18
since upgrading from hoary -> breezy some of my Java apps under development are choking on the new mysqld server 4.1.12 

I've raised the issue (stuffed with some test results) over in mysql land:
[http://forums.mysql.com/read.php?39,49989,49989#msg-49989](http://forums.mysql.com/read.php?39,49989,49989#msg-49989)
(people seeking for a stopgap should read there)

only to find people there doubthing the gcc/glibc used in debian circles for compiling the 4.1. mysql server package. (whatever that may mean)

From where I stand I'ld have to say the blatant simplicity of my test (default package install/standard jdbc procedure/basic datatypes) really does hint towards some real core setting missing during the assembly of the package... but hey YMMV

Anyways, assuming this leads us indeed down the yellow brick road to fixing the package: Does anyone know where this should be taken?

---

### Post by wimva on 2005-11-16
Hi, just adding my 2 cents here. Recently I had the following experience. While using an OpenOffice.org 2 Base document connecting via jdbc to a fresh MySQL apt installation on Breezy I was suddenly confronted with strange "empty result set" error messages. 

Very strange, since I could verify with the mysqlclient that my data was there. One point of interest : I recently upgraded from Hoary where the same operation worked like a charm. 

Another interesting fact : the stopgap solution of mpo (using useServerPrepStmts=false on the jdbc url) made everything working on Breezy! 

It is even possible to reconstruct this behaviour using the same OpenOffice.org 2 Base document on a Windows XP computer connecting to the Breezy MySQL database using the standard port 3306. So using no Java on the Breezy server. 

Doesn't this seem to indicate that the MySQL version installed using good old apt on Breezy does introduce some unwanted side effects. I hope someone can have a look into this because I do like apt installations.

---

