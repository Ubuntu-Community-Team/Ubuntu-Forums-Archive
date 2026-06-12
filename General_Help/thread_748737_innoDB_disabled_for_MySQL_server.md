---
title: "innoDB disabled for MySQL server"
date: 2008-04-07
forum: General Help
---

### Post by skunkwerk on 2008-04-07
I'm trying to use innoDB instead of MyISAM in MySQL, however when I log in with phpmyadmin and click on Engines and then InnoDB, I get this message:
InnoDB has been disabled for this MySQL server. 

I'm running ubuntu 7.10 and installed mysql-server mysql-client mysql-common with apt-get.  the /etc/mysql/my.cnf file states that innodb will be enabled by default when the database size is larger than 10 MB, but i'd like to do that now as I don't trust it to work.  I've also added 'default-storage-engine=innodb' to the end of my.cnf and restarted mysql, but that hasn't made a difference.

any suggestions?
thanks

---

### Post by geedew on 2008-05-21
Try this, I was having the same issues today...

[http://geedew.com/blog/2008/05/21/how-to-fix-innodb-has-been-disabled-for-this-mysql-server/](http://geedew.com/blog/2008/05/21/how-to-fix-innodb-has-been-disabled-for-this-mysql-server/)

---

### Post by dughutch on 2008-07-03
Bump

Same issue... was trying to install MySQL and Hyperic requires InnoDB... but I was unable to "force" InnoDB "on"... 

Is there a way to turn innodb on by default so that it shows active in phpmyadmin?

Is there any relation to the fact that the other InnoDB variables also seemed to not accurately reflect the values in my.cnf.... specifically innodb_buffer_pool_size = 256M ... phpmyadmin always showed 8M...

---

