---
title: "Having trouble getting MySQL working"
date: 2005-04-14
forum: General Help
---

### Post by now departed on 2005-04-14
Hi,

After I got the connection between OOo 1.1.2 and MySQL 4.0.something working under Ubuntu 4.1 ,I discoverved that before the 4.1 release of MySQL it's not possible to use subqueries.
I Hoped the in the Hoary distrib it was the MySQL 4.1... Well, Wrong guess. So I decided to install it without synaptic and taking care of removing the previous version with synaptic.
I did everything mentioned in the BINARY-INSTALL file coming with the MySQL package meaning the following :

The basic commands you must execute to install and use a MySQL binary
distribution are:

     shell> groupadd mysql
     shell> useradd -g mysql mysql
     shell> cd /usr/local
     shell> gunzip < /PATH/TO/MYSQL-VERSION-OS.tar.gz | tar xvf -
     shell> ln -s FULL-PATH-TO-MYSQL-VERSION-OS mysql
     shell> cd mysql
     shell> scripts/mysql_install_db --user=mysql
     shell> chown -R root  .
     shell> chown -R mysql data
     shell> chgrp -R mysql .
     shell> bin/mysqld_safe --user=mysql &

For versions of MySQL older than 4.0, substitute `bin/safe_mysqld' for
`bin/mysqld_safe' in the final command.

and I get this :
 Starting mysqld daemon with databases from /usr/local/mysql/data
bin/safe_mysqld: line 311: /usr/local/mysql/data/parents-ubuntu.err: Permission non accordée
rm: ne peut enlever `/usr/local/mysql/data/parents-ubuntu.pid': Permission non accordée
bin/safe_mysqld: line 317: /usr/local/mysql/data/parents-ubuntu.err: Permission non accordée
STOPPING server from pid file /usr/local/mysql/data/parents-ubuntu.pid
tee: /usr/local/mysql/data/parents-ubuntu.err: Permission non accordée
050414 16:58:11  mysqld ended
tee: /usr/local/mysql/data/parents-ubuntu.err: Permission non accordée

For the non french speaking souls permission non accordée means something like priviledges not granted

then I copied the mysql.server file in the /etc.init.d directory and created the sym links toward the directories as indicated in the mysql.server script to have the server launched at boot time. It does not work.

Any help welcome. 

MOOD
I have been trying to use linux for more than a year because I like the challenge of discovering new stuffs and also because I like the way that linux is trying to get people a little bit more intelligent by having them sort of involved in things trying to make things open (as opposed to hiden) which I think windows does not do. 
BUT I feel immensely frustrated because I have spent more time having things working than actually using them =;

---

