---
title: "[SOLVED] Error installing PDO_MYSQL"
date: 2007-11-29
forum: General Help
---

### Post by alimadzi on 2007-11-29
I'm getting a strange error when I try to run 'pecl install pdo_mysql'.  The PDO package is already installed and I added the 'extension=pdo.so' line to php.ini and reloaded Apache2.  Here's the error I'm getting:

```

root@extra:/var/www# pecl install pdo_mysql
downloading PDO_MYSQL-1.0.2.tgz ...
Starting to download PDO_MYSQL-1.0.2.tgz (14,778 bytes)
.....done: 14,778 bytes
7 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20050922
Zend Extension Api No:   220051025
building in /var/tmp/pear-build-root/PDO_MYSQL-1.0.2
running: /tmp/pear/download/PDO_MYSQL-1.0.2/configure
checking for egrep... grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking whether gcc and cc understand -c and -o together... yes
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext
checking for PHP extension directory... /usr/lib/php5/20051025
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... re2c
checking for re2c version... 0.9.12 (ok)
checking for gawk... gawk
checking for MySQL support for PDO... yes, shared
checking for mysql_config... /usr/bin/mysql_config
checking for mysql_query in -lmysqlclient... yes
checking for mysql_commit... yes
checking for mysql_stmt_prepare... yes
checking for mysql_next_result... yes
checking for mysql_sqlstate... yes
checking for PDO includes... checking for PDO includes... /usr/include/php/ext
configure: error:
You've configured extension pdo_mysql, which depends on extension pdo,
but you've either not enabled pdo, or have disabled it.

ERROR: `/tmp/pear/download/PDO_MYSQL-1.0.2/configure' failed

```

What should I do to fix this?  Is there another step to enabling PDO so I can add the DB-specific extensions?  Thanks.

-Patrick

---

### Post by alimadzi on 2007-11-29
Found a solution using The Google...

[http://pecl.php.net/bugs/bug.php?id=6117](http://pecl.php.net/bugs/bug.php?id=6117)

The magic command is...

```

PHP_PDO_SHARED=1 pecl install PDO_xxx

```

Replace the 'xxx' with your desired DB like 'mysql' or 'sqlite'.  Enjoy!

-Patrick

---

