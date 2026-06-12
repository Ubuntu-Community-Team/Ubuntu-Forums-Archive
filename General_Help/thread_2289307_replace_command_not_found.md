---
title: "replace command not found"
date: 2015-08-03
forum: General Help
---

### Post by bizhat on 2015-08-03
I have a program that use /usr/bin/replace, this is part of mysql. I think recent mysql upgrades removed it.

```

root@fwhlin:~ # which replace
root@fwhlin:~ # replace
The program 'replace' can be found in the following packages:
 * mysql-server-5.5
 * mariadb-server-5.5
 * mysql-server-5.6
 * percona-xtradb-cluster-server-5.5
Try: apt-get install <selected package>
root@fwhlin:~ # dpkg -S /usr/bin/replace
dpkg-query: no path found matching pattern /usr/bin/replace
root@fwhlin:~ # 

```

I have mysql installed.

```

root@fwhlin:~ # dpkg -l | grep mysql
ii  libdbd-mysql-perl                                     4.025-1                                                amd64        Perl5 database interface to the MySQL database
ii  libmysqlclient-dev                                    5.5.43-0ubuntu0.14.04.1                                amd64        MySQL database development files
ii  libmysqlclient18:amd64                                5.5.43-0ubuntu0.14.04.1                                amd64        MySQL database client library
ii  libmysqlclient18:i386                                 5.5.43-0ubuntu0.14.04.1                                i386         MySQL database client library
ii  libqt4-sql-mysql:i386                                 4:4.8.5+git192-g085f851+dfsg-2ubuntu4.1                i386         Qt 4 MySQL database driver
ii  mysql-client-5.5                                      5.5.43-0ubuntu0.14.04.1                                amd64        MySQL database client binaries
ii  mysql-client-core-5.5                                 5.5.43-0ubuntu0.14.04.1                                amd64        MySQL database core client binaries
ii  mysql-common                                          5.5.43-0ubuntu0.14.04.1                                all          MySQL database common files, e.g. /etc/mysql/my.cnf
rc  mysql-server-5.5                                      5.5.38-0ubuntu0.14.04.1                                amd64        MySQL database server binaries and system database setup
ii  mysql-server-core-5.5                                 5.5.43-0ubuntu0.14.04.1                                amd64        MySQL database server binaries
ii  php5-mysql                                            5.5.9+dfsg-1ubuntu4.9                                  amd64        MySQL module for php5
ii  python-mysqldb                                        1.2.3-2ubuntu1                                         amd64        Python interface to MySQL
ii  python3-mysql.connector                               1.1.6-1                                                all          pure Python implementation of MySQL Client/Server protocol (Python3)
root@fwhlin:~ # 

```

I am using  Ubuntu 14.04.2 LTS

Is there anyway i can get the replace command back ?

---

### Post by kerry_s on 2015-08-03
have you checked in /bin & /usr/sbin ?

---

### Post by bizhat on 2015-08-03
Yes

```

root@fwhlin:~ # ls -l /bin /sbin /usr/local/bin /usr/bin | grep replace
root@fwhlin:~ # 

```

dpkg -L mysql-client-5.5 do not show replace.

```

root@fwhlin:~ # dpkg -L mysql-client-5.5
/.
/usr
/usr/bin
/usr/bin/innotop
/usr/bin/mysqladmin
/usr/bin/mysqlaccess
/usr/bin/mysqldump
/usr/bin/mysqlshow
/usr/bin/mysqlbug
/usr/bin/mysql_waitpid
/usr/bin/mysqlimport
/usr/bin/mysqlreport
/usr/bin/mysql_find_rows
/usr/bin/mysqldumpslow
/usr/bin/mysqlslap
/usr/bin/myisam_ftdump
/usr/bin/mysql_fix_extensions
/usr/bin/innochecksum
/usr/bin/mysql_plugin
/usr/bin/mysql_client_test
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/mysql-client-5.5
/usr/share/doc
/usr/share/doc/mysql-client-5.5
/usr/share/doc/mysql-client-5.5/copyright
/usr/share/doc/mysql-client-5.5/README
/usr/share/doc/mysql-client-5.5/README.Debian
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/mysql_fix_extensions.1.gz
/usr/share/man/man1/mysql_waitpid.1.gz
/usr/share/man/man1/mysqlbug.1.gz
/usr/share/man/man1/mysqldumpslow.1.gz
/usr/share/man/man1/mysqlslap.1.gz
/usr/share/man/man1/mysql_plugin.1.gz
/usr/share/man/man1/myisam_ftdump.1.gz
/usr/share/man/man1/mysql_client_test_embedded.1.gz
/usr/share/man/man1/mysqldump.1.gz
/usr/share/man/man1/mysqlman.1.gz
/usr/share/man/man1/mysqlreport.1.gz
/usr/share/man/man1/innotop.1.gz
/usr/share/man/man1/mysql_tableinfo.1.gz
/usr/share/man/man1/mysql_client_test.1.gz
/usr/share/man/man1/mysqlshow.1.gz
/usr/share/man/man1/mysqlaccess.1.gz
/usr/share/man/man1/mysql_find_rows.1.gz
/usr/share/man/man1/mysqlimport.1.gz
/usr/share/man/man1/mysqladmin.1.gz
/usr/bin/mysqloptimize
/usr/bin/mysqlanalyze
/usr/bin/mysqlrepair
/usr/share/doc/mysql-client-5.5/changelog.Debian.gz
/usr/share/doc/mysql-client-5.5/NEWS.Debian.gz
/usr/share/man/man1/mysqlanalyze.1.gz
/usr/share/man/man1/mysqloptimize.1.gz
/usr/share/man/man1/mysqlrepair.1.gz
root@fwhlin:~ # 

```

mysql version is

```

root@fwhlin:~ # mysql --version
mysql  Ver 14.14 Distrib 5.5.43, for debian-linux-gnu (x86_64) using readline 6.3
root@fwhlin:~ # 

```

---

### Post by kerry_s on 2015-08-03
doesn't "sed" do the same thing as "replace" command ?
"replace" came from dos/windows back in the day, never used in linux. lol, yeah, i'm old.

---

### Post by bizhat on 2015-08-03
sed can do, but this is dependency for another program i am using, if there is no solution, i have to update the code to make it work with sed, that need me to do the debugging.

---

