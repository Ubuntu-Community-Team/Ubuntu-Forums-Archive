---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-10-14
forum: General Help
---

### Post by tonma on 2016-10-14
I wanted to install a new LAMP stack on another hard drive, and try MariaDB, so I followed this guide:
[https://www.unixmen.com/how-to-install-lamp-stack-on-ubuntu-16-04/](https://www.unixmen.com/how-to-install-lamp-stack-on-ubuntu-16-04/)

The only thing I did differently than the guide was that instead of first installing MySQL, I jumped straight to the "sudo apt-get install mariadb-server", without first installing MySQL and then doing the removal procedure.

Then, I wanted to switch back to MySQL, so I did stuff like purge and autoclean to MariaDB.

Since then I've had issues: When I do now sudo apt-get install mysql-server, I get this error:

Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

I do get to the configuration part of the MySQL installaton, where I need to set a root password, but nothing more.

I think it has to do something with MariaDB, because I can still log in to phpMyAdmin with my MariaDB 'root' user and its password (I set a different password for the MySQL 'root' user just to check)

Any idea how to fix that? And how to completely remove MariaDB? Why can I still log in to phpMyAdmin with it after purging it?

Thanks!

---

### Post by T.J. on 2016-10-15
> **tonma said:**
> I wanted to install a new LAMP stack on another hard drive, and try MariaDB, so I followed this guide:
[https://www.unixmen.com/how-to-install-lamp-stack-on-ubuntu-16-04/](https://www.unixmen.com/how-to-install-lamp-stack-on-ubuntu-16-04/)

The only thing I did differently than the guide was that instead of first installing MySQL, I jumped straight to the "sudo apt-get install mariadb-server", without first installing MySQL and then doing the removal procedure.

Then, I wanted to switch back to MySQL, so I did stuff like purge and autoclean to MariaDB.

Since then I've had issues: When I do now sudo apt-get install mysql-server, I get this error:

Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

I do get to the configuration part of the MySQL installaton, where I need to set a root password, but nothing more.

I think it has to do something with MariaDB, because I can still log in to phpMyAdmin with my MariaDB 'root' user and its password (I set a different password for the MySQL 'root' user just to check)

Any idea how to fix that? And how to completely remove MariaDB? Why can I still log in to phpMyAdmin with it after purging it?

Thanks!


That usually means an incomplete install or bad package.  IMHO you should file a bug report. To answer your question, probably because it is still active and was not uninstalled properly.

---

### Post by ian-weisser on 2016-10-15
Please show us the complete output of a session where you (re-)uninstall mariadb and try to install mysql

---

### Post by tonma on 2016-10-15
Thanks guys! eventually it did work, I did the following:

sudo apt-get purge mysql* mariadb*, and it worked! (with the asterisk. At first I purged without it)

---

