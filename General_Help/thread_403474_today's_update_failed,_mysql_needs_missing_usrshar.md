---
title: "today's update failed, mysql needs missing /usr/share/mysql"
date: 2007-04-07
forum: General Help
---

### Post by Georges on 2007-04-07
edgy 6.10

I ran the autoupdate and it failed on mysql-server-5.0

chown: cannot access `/usr/share/mysql': No such file or directory

And starting the server:
070407  9:22:29 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'

# dpkg -L mysql-server-5.0|grep share|wc
      0       0       0

# dpkg -S errmsg.sys
dpkg: *errmsg.sys* not found.

Ermm, yeah... something is missing.

```

 # dpkg -l|grep mysql
ii  libdbd-mysql-perl                      3.0006-1                              A Perl5 database interface to the MySQL data
ii  libmysqlclient10                       3.23.56-3                             LGPL-licensed client library for MySQL datab
ii  libmysqlclient12                       4.0.24-10ubuntu2.3                    mysql database client library
ii  libmysqlclient14                       4.1.15-1ubuntu5                       mysql database client library
ii  libmysqlclient15off                    5.0.24a-9ubuntu2                      mysql database client library
ii  mysql-client-5.0                       5.0.24a-9ubuntu2                      mysql database client binaries
ii  mysql-common                           5.0.24a-9ubuntu2                      mysql database common files (e.g. /etc/mysql
iU  mysql-server                           5.0.24a-9ubuntu2                      mysql database server (current version)
iF  mysql-server-5.0                       5.0.24a-9ubuntu2                      mysql database server binaries
ii  php4-mysql                             4.4.2-1.1                             MySQL module for php4
ii  python-mysqldb                         1.2.1c3-4ubuntu4                      A Python interface to MySQL
ii  python2.4-mysqldb                      1.2.1c3-4ubuntu4                      A Python interface to MySQL

```

# uname -a
Linux storm 2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux

---

