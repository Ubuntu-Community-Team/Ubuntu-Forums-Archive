---
title: "PHP4 MySQL Support"
date: 2005-06-09
forum: General Help
---

### Post by C03N on 2005-06-09
Is there an option to enable MySQL support when installing PHP4 via apt-get?

**PHPINFO**
'../configure' '--prefix=/usr' '--with-apxs2=/usr/bin/apxs2' '--with-config-file-path=/etc/php4/apache2' '--enable-memory-limit' '--disable-debug' '--with-regex=php' '--disable-rpath' '--disable-static' '--with-pic' '--with-layout=GNU' '--with-pear=/usr/share/php' '--enable-calendar' '--enable-sysvsem' '--enable-sysvshm' '--enable-sysvmsg' '--enable-track-vars' '--enable-trans-sid' '--enable-bcmath' '--with-bz2' '--enable-ctype' '--with-db4' '--with-iconv' '--enable-exif' '--enable-filepro' '--enable-ftp' '--with-gettext' '--enable-mbstring' '--with-pcre-regex=/usr' '--enable-shmop' '--enable-sockets' '--enable-wddx' '--disable-xml' '--with-expat-dir=/usr' '--with-xmlrpc' '--enable-yp' '--with-zlib' '--without-pgsql' '--with-kerberos=/usr' '--with-openssl=/usr' '--enable-dbx' '--with-mime-magic=/usr/share/misc/file/magic.mime' '--with-exec-dir=/usr/lib/php4/libexec' '--without-mm' '**--without-mysql**' '--without-sybase-ct'

The [COLOR=Red]error[/COLOR] I am getting is: 
**Fatal error:** Call to undefined function: mysql__connect()

This is described as a common problem on the MySQL Site ([http://dev.mysql.com/doc/mysql/en/php-problems.html)](http://dev.mysql.com/doc/mysql/en/php-problems.html))...

...Error: "Fatal error: Call to unsupported or undefined function mysql_connect() in .." This means that your PHP version isn't compiled with MySQL support. You can either compile a dynamic MySQL module and load it into PHP or recompile PHP with built-in MySQL support. This is described in detail in the PHP manual.

I followed the instructions on the **Unofficial Ubuntu 5.04 Starter Guide** Web Site to install:

Apache2
MySQL-4.1
MySQLCC
PHP4
PHP4-MYSQL
libapache2-mod-auth-mysql

---

### Post by defkewl on 2005-06-09
Did you try:
$ apt-get upgrade php-mysql

---

### Post by C03N on 2005-06-10
I ran the command you asked about and pasted the output below.

# apt-get upgrade php-mysql
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  mozilla-firefox mozilla-firefox-gnome-support
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

apt-get upgrade produces the same output. I'm pretty sure you're not supposed to append a package name when using upgrade, as it updates *all packages.

*** man page description of upgrade**
upgrade  is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. 
Packages currently installed with new versions available  are retrieved  and  upgraded; under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be up-graded  without changing  the install status of another package will be left at their current version.

---

### Post by C03N on 2005-06-13
**?** :-?

---

### Post by momo66 on 2005-06-13
[QUOTE=C03N]Is there an option to enable MySQL support when installing PHP4 via apt-get?

I just loaded xampp distribution which includes apache, mysql, php 4 and 5, perl, and whole bunch of tools.

It literally takes about 5 minutes to install.  I have gone through the process of installing them individually and it was a chore.  The xampp package made it so much less painful.

[www.apachefriends.org/en/xampp.html](www.apachefriends.org/en/xampp.html)

---

### Post by crun on 2005-06-13
C03N, you did
```
sudo apt-get upgrade php-mysql
``` 
which just upgrades your installed packages. What you're looking for is
```
sudo apt-get install php4-mysql
``` 
(I assume you're using php4 here - if not, try another version number of php-mysql).

After you've installed it, go to your php.ini file (probably in /etc/php4/apache2/php.ini) and look for the line
```
mysql.so
```
and remove the comments. Restart Apache with
```
sudo apache2ctl restart
``` 
and mysql should work

---

### Post by reid on 2005-06-14
crun,
Thanks, that solved my problem also.

It is much appreciated.

---

