---
title: "php mysql apache on Ubuntu"
date: 2005-03-25
forum: General Help
---

### Post by andreabg on 2005-03-25
Hello,

I want to install php myswl apache2 on my ubuntu 4.10.
I'm not connected to internet so I've downloaded the three programs from another pc.

So I've got the .tar.gz files.

With Apache2 no problem: I've unpacked .tar.gz file, made ./configure and then make.

Apache2 works regularly

When I try to install Mysql I've got problems:
I'm succesfull in unpacking files and also with ./configure, but when I type make I've got an error that says me that make command is not found?

Why make it ok with Apache and not with Mysql?

I'm working with ubuntu 4.10 ppc version

Thanks for help

Andrea

---

### Post by xianfa on 2005-03-25
Andrea,

I have done this very same install about a dozen times. Here are the steps I follow to get success.

1. Install Zlib
tar -xvzf zlib-(version).tar.gz
cd zlib
./configure; make test
make install

2. Install MySQL
groupadd mysql
useradd -g mysql mysql
tar -xvzf mysql-(version).tar.gz
cd mysql
./configure --prefix=/usr/local/mysql
make
make install
scripts/mysql_install_db
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/var
chgrp -R mysql /usr/local/mysql
add /usr/local/mysql/lib/mysql and /usr/local/lib to /etc/ld.so.conf
then run ldconfig -v "as root"

3. Install Apache and PHP
tar -xvzf httpd-(version).tar.gz
cd httpd-(version)
./configure --prefix=/www --enable-sockets
make
make install
cd ..
tar -xvzf php-(version).tar.gz
cd php-(version)
./configure --prefix=/www/php --with-apxs2=/www/bin/apxs --with-config-file-path=/www/php --enable-sockets --with-mysql=/usr/local/mysql --with-zlib-dir=/usr/local --with-gd (all one line)
make
make install
cp php.ini-dist /www/php/php.ini

4. Edit httpd.conf file
vi /www/conf/httpd.conf
ctrl-w AddType and add:
AddType application/x-tar .tgz
AddType image/x-icon .ico
AddType application/x-httpd-php .php
then ctrl-w DirectoryIndex and add:
index.php index.html index.html.var

5. Setup mysql and apache to start automatically
cp (mysql-(version))support-files/mysql.server /etc/init.d/mysql
cd /etc/rc3.d
ln -s ../init.d/mysql S85mysql
ln -s ../init.d/mysql K85mysql
cd /etc/rc5.d
ln -s ../init.d/mysql S85mysql
ln -s ../init.d/mysql K85mysql
cd ../init.d
chmod 755 mysql
cp /www/bin/apachectl /etc/init.d/httpd
cd /etc/rc3.d
ln -s ../init.d/httpd S85httpd
ln -s ../init.d/httpd K85httpd
cd /etc/rc5.d
ln -s ../init.d/httpd S85httpd
ln -s ../init.d/httpd K85httpd

This should get you up and running.

Brian McCoy


>Hello,
>
>I want to install php myswl apache2 on my ubuntu 4.10.
>I'm not connected to internet so I've downloaded the three programs from >another pc.
>
>So I've got the .tar.gz files.
>
>With Apache2 no problem: I've unpacked .tar.gz file, made ./configure and then >make.
>
>Apache2 works regularly
>
>When I try to install Mysql I've got problems:
>I'm succesfull in unpacking files and also with ./configure, but when I type make >I've got an error that says me that make command is not found?
>
>Why make it ok with Apache and not with Mysql?
>
>I'm working with ubuntu 4.10 ppc version
>
>Thanks for help
>
>Andrea

---

### Post by xianfa on 2005-03-25
Andrea,

I forgot to add, you will have to install some development libraries. when you get an error during ./configure, it will specify at the point it stops that you are missing a specific program. Go to the Synaptic Package Manager and download the requirements and try the ./configure again until all the dependancies are met.

Brian McCoy

[QUOTE=xianfa]Andrea,

I have done this very same install about a dozen times. Here are the steps I follow to get success.

1. Install Zlib
tar -xvzf zlib-(version).tar.gz
cd zlib
./configure; make test
make install

2. Install MySQL
groupadd mysql
useradd -g mysql mysql
tar -xvzf mysql-(version).tar.gz
cd mysql
./configure --prefix=/usr/local/mysql
make
make install
scripts/mysql_install_db
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/var
chgrp -R mysql /usr/local/mysql
add /usr/local/mysql/lib/mysql and /usr/local/lib to /etc/ld.so.conf
then run ldconfig -v "as root"

3. Install Apache and PHP
tar -xvzf httpd-(version).tar.gz
cd httpd-(version)
./configure --prefix=/www --enable-sockets
make
make install
cd ..
tar -xvzf php-(version).tar.gz
cd php-(version)
./configure --prefix=/www/php --with-apxs2=/www/bin/apxs --with-config-file-path=/www/php --enable-sockets --with-mysql=/usr/local/mysql --with-zlib-dir=/usr/local --with-gd (all one line)
make
make install
cp php.ini-dist /www/php/php.ini

4. Edit httpd.conf file
vi /www/conf/httpd.conf
ctrl-w AddType and add:
AddType application/x-tar .tgz
AddType image/x-icon .ico
AddType application/x-httpd-php .php
then ctrl-w DirectoryIndex and add:
index.php index.html index.html.var

5. Setup mysql and apache to start automatically
cp (mysql-(version))support-files/mysql.server /etc/init.d/mysql
cd /etc/rc3.d
ln -s ../init.d/mysql S85mysql
ln -s ../init.d/mysql K85mysql
cd /etc/rc5.d
ln -s ../init.d/mysql S85mysql
ln -s ../init.d/mysql K85mysql
cd ../init.d
chmod 755 mysql
cp /www/bin/apachectl /etc/init.d/httpd
cd /etc/rc3.d
ln -s ../init.d/httpd S85httpd
ln -s ../init.d/httpd K85httpd
cd /etc/rc5.d
ln -s ../init.d/httpd S85httpd
ln -s ../init.d/httpd K85httpd

This should get you up and running.

Brian McCoy


>Hello,
>
>I want to install php myswl apache2 on my ubuntu 4.10.
>I'm not connected to internet so I've downloaded the three programs from >another pc.
>
>So I've got the .tar.gz files.
>
>With Apache2 no problem: I've unpacked .tar.gz file, made ./configure and then >make.
>
>Apache2 works regularly
>
>When I try to install Mysql I've got problems:
>I'm succesfull in unpacking files and also with ./configure, but when I type make >I've got an error that says me that make command is not found?
>
>Why make it ok with Apache and not with Mysql?
>
>I'm working with ubuntu 4.10 ppc version
>
>Thanks for help
>
>Andrea[/QUOTE]

---

### Post by andreabg on 2005-03-25
Hello xianfa,

thanks for yr instruction.
I've followed them but when I reach:

2. Install MySQL
groupadd mysql
useradd -g mysql mysql
tar -xvzf mysql-(version).tar.gz
cd mysql
./configure --prefix=/usr/local/mysql
make

after typing make I've got the following error:

*No target specified and no makefile found Stop* 

 ](*,)  ](*,)  ](*,) 

Any suggestion?

Thanks
Andrea

---

### Post by xianfa on 2005-03-25
Andria,

It sounds like the ./configure isn't finishing. Make sure you read the last line after typing the ./configure command. I will almost guarantee it isn't finishing. If the ./configure doesn'tr finish, it won't create the Makefile, the ./configure process is what creates the makefile.

[QUOTE=andreabg]Hello xianfa,

thanks for yr instruction.
I've followed them but when I reach:

2. Install MySQL
groupadd mysql
useradd -g mysql mysql
tar -xvzf mysql-(version).tar.gz
cd mysql
./configure --prefix=/usr/local/mysql
make

after typing make I've got the following error:

*No target specified and no makefile found Stop* 

 ](*,)  ](*,)  ](*,) 

Any suggestion?

Thanks
Andrea[/QUOTE]

---

### Post by andreabg on 2005-03-25
Xianfa,

the last line after typing ./configure tells:

*checking for termcap functions library................. configure:error: No curses/termcap library found* 

I suppose I've to install termcap library that I think are part of ncurses-dev, right??

I've got ncurses version 5.4-4, so where to find ncurses-dev? 

Thanks
Andrea

---

### Post by andreabg on 2005-03-26
Wow!!

I've downoladed libncurses5-dev_5.4-4_powerpc.deb from Debian, installed them and now everything works.

 \\:D/  \\:D/ 

thanks xianfa for yr precious suggestions

Andrea

---

### Post by az on 2005-03-26
All that and you just should have done:

sudo apt-get install apache2 mysql-server php4

---

### Post by magnet on 2005-04-08
Hello, sorry for my English.
this is my first introduccion in linux system.

I have a litel problem. I need install the additional .ini files parsed.
I install with Synaptic de apache2 and modules for Php and sql. And all is working, thw web, de php, but phpmyadmin say this:

[1.20] I receive the error "cannot load MySQL extension, please check PHP Configuration".

To connect to a MySQL server, PHP needs a set of MySQL functions called "MySQL extension". This extension may be part of the PHP distribution (compiled-in), otherwise it needs to be loaded dynamically. Its name is probably mysql.so or php_mysql.dll. phpMyAdmin tried to load the extension but failed.

Usually, the problem is solved by installing a software package called "PHP-MySQL" or something simila

I don't now who install this extension.
And I don't nowk who can now, the place where I have the MySQL .

thank's a lot

---

### Post by macewan on 2005-04-10
magnet - I went through the same situation yesterday and this morning while installing WordPress 1.5 on Hoary.

Try to uncomment the route with the removal of

sudo vi +536 /etc/php4/apache2/php.ini

remove **;**from in front of extension=mysql.so

as stated from above post - save and then **sudo apt-get install phpmyadmin**

this at least worked for me after much headache

---

### Post by magnet on 2005-04-11
Thank's a lot, but this is the first thing that I do but don't work, I suppose I need re-complile with this optin, but I install this directli with Synaptic, I don't now if I can compile only this extension, o with the config file I can, ...

I the info.php I want install something like this:
**additional .ini files parsed **	/etc/php.d/imap.ini, /etc/php.d/ldap.ini, /etc/php.d/mysql.ini, /etc/php.d/odbc.ini

But in my computer this no aperrs.

I try tinstall phpmyadmin with apt-get install phpmyadmin, but say me that the paket is not found, 



thants alot

---

### Post by andreabg on 2005-04-11
Hello,

try this link and you'll find phpmyadmin deb package: [http://packages.debian.org/stable/web/phpmyadmin](http://packages.debian.org/stable/web/phpmyadmin)

I've also have the error message:

[I][COLOR=Red]"cannot load MySQL extension, please check PHP Configuration".

To connect to a MySQL server, PHP needs a set of MySQL functions called "MySQL extension". This extension may be part of the PHP distribution (compiled-in), otherwise it needs to be loaded dynamically. Its name is probably mysql.so or php_mysql.dll. phpMyAdmin tried to load the extension but failed[/COLOR].[/I]

I've tried so many times and no success.

Has anyone been succesfull?
What have I to do?
 :? 

Thanks
Andrea

---

### Post by akinwale on 2005-04-18
[QUOTE=azz]All that and you just should have done:

sudo apt-get install apache2 mysql-server php4[/QUOTE]


Well, uh... I actually prefer to compile from source in cases as this, because
Reason 1: The application runs faster
Reason 2: More customisation, I can compile with the options I want

But that's just me ;)

---

### Post by Infernal on 2005-04-19
[QUOTE=akinwale]Well, uh... I actually prefer to compile from source in cases as this, because
Reason 1: The application runs faster
Reason 2: More customisation, I can compile with the options I want

But that's just me ;)[/QUOTE]
 i've tried every step in this post, but i still get the same error as andreabg

---

### Post by flightcrank on 2005-04-28
thanks u guys saved me alot of time, mine works now also, however you should not have to install phpmyadmin at all for word press to work, so its strange that we have to on ubuntu, oh well it works

---

### Post by sorca on 2005-05-02
Hi,

I am struggeling with phpmyadmin and get the same error as above. I tried to install the phpmyadmin deb but it didn't work telling me php4-mysql wasn't installed. I have tried to install [COLOR=Red]php4-mysql_4.1.2-7.0.1_i386.deb
[/COLOR] but get an error that it depends on [COLOR=Red]zendapi-20010901[/COLOR]. And this package is, according to packages.debian.org, virtual and included in php4 and php4-cgi. I have both installed.

When I try [COLOR=Red]apt-get install php4[/COLOR] i get the message that it cannot be completed due to phpmyadmin not being installed and that this depends on [COLOR=Red]wwwconfig-common (>=0.0.7)[/COLOR]. When I search apckages for it i find only version 0.0.43.

I feel like I am in a dead end...could anyone lend me some advice?

/Oscar  ](*,)

---

### Post by OuR_LanD on 2005-05-06
I know this may be late or irrelivant but you could see if there is a version of 'PHP Triad' avaliable for Linux. This package installs Apache with PHP and MySql in one go. I have it installed on windows and its a nice neat package. I hope this helps in someone in some way.

---

