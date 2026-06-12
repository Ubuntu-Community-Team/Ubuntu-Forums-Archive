---
title: "problem with apache2 on Ubuntu"
date: 2007-08-21
forum: General Help
---

### Post by iwegbue@gmail.com on 2007-08-21
My apache2 on Ubuntu is not working properly and I'm not sure why. When the system is booting up, i notice that apache2 restat fails; same thing happens when the system is shutting down. I've tried to re-install apache with:


sudo apt-get install --reinstall apache2 apache2-common apache2-mpm-worker apache2-utils libapr0 ssl-cert

but i get the following:

home:~$ sudo apt-get install --reinstall apache2 apache2-common apache2-mpm-worker apache2-utils libapr0 ssl-cert
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  apache2-mpm-prefork libapache2-mod-php5 php5 php5-mysql php5-mysqli
The following NEW packages will be installed:
  apache2-mpm-worker
0 upgraded, 1 newly installed, 5 reinstalled, 5 to remove and 0 not upgraded.
Need to get 212kB/1257kB of archives.
After unpacking 5501kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main apache2-mpm-worker 2.0.55-4ubuntu2.2 [202kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ssl-cert 1.0.13 [9526B]
Fetched 212kB in 1s (147kB/s)
Preconfiguring packages ...
(Reading database ... 89426 files and directories currently installed.)
Removing php5 ...
Removing php5-mysql ...
Removing php5-mysqli ...
Removing libapache2-mod-php5 ...
Module php5 disabled; run /etc/init.d/apache2 force-reload to fully disable.
(Reading database ... 89419 files and directories currently installed.)
Preparing to replace apache2 2.0.55-4ubuntu2.2 (using .../apache2_2.0.55-4ubuntu2.2_i386.deb) ...
Unpacking replacement apache2 ...
dpkg: apache2-mpm-prefork: dependency problems, but removing anyway as you request:
 websvn depends on apache2 | httpd; however:
  Package apache2 is not configured yet.
  Package apache2-mpm-prefork which provides apache2 is to be removed.
  Package httpd is not installed.
  Package apache2-mpm-prefork which provides httpd is to be removed.
 websvn depends on apache2 | httpd; however:
  Package apache2 is not configured yet.
  Package apache2-mpm-prefork which provides apache2 is to be removed.
  Package httpd is not installed.
  Package apache2-mpm-prefork which provides httpd is to be removed.
(Reading database ... 89418 files and directories currently installed.)
Removing apache2-mpm-prefork ...
 * Stopping apache 2.0 web server...                                     [fail]
invoke-rc.d: initscript apache2, action "stop" failed.
Selecting previously deselected package apache2-mpm-worker.
(Reading database ... 89415 files and directories currently installed.)
Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.0.55-4ubuntu2.2_i386.deb) ...
Preparing to replace apache2-common 2.0.55-4ubuntu2.2 (using .../apache2-common_2.0.55-4ubuntu2.2_i386.deb) ...
Unpacking replacement apache2-common ...
Preparing to replace apache2-utils 2.0.55-4ubuntu2.2 (using .../apache2-utils_2.0.55-4ubuntu2.2_i386.deb) ...
Unpacking replacement apache2-utils ...
Preparing to replace libapr0 2.0.55-4ubuntu2.2 (using .../libapr0_2.0.55-4ubuntu2.2_i386.deb) ...
Unpacking replacement libapr0 ...
Preparing to replace ssl-cert 1.0.13 (using .../ssl-cert_1.0.13_all.deb) ...
Unpacking replacement ssl-cert ...
Setting up libapr0 (2.0.55-4ubuntu2.2) ...

Setting up ssl-cert (1.0.13) ...

Setting up apache2-utils (2.0.55-4ubuntu2.2) ...
Setting up apache2-common (2.0.55-4ubuntu2.2) ...

Setting up apache2-mpm-worker (2.0.55-4ubuntu2.2) ...
 * Starting apache 2.0 web server... Syntax error on line 15 of /etc/apache2/conf.d/freemed.conf:
Cannot load /etc/apache2/modules/libphp4.so into server: /etc/apache2/modules/libphp4.so: cannot open shared object file: No such file or directory
                                                                         [fail]
invoke-rc.d: initscript apache2, action "start" failed.


Any ideas??

---

### Post by glasswalkerny on 2007-08-22
I'm not an expert by a long shot but here's my take on your problem....

Did you install PHP4 with the apache server? it looks like from this error > Cannot load /etc/apache2/modules/libphp4.so into server: /etc/apache2/modules/libphp4.so: cannot open shared object file: No such file or directory
[fail]
 that you are missing the PHP4 library. Now if you're running Feisty PHP4 is not in the repositories but PHP5 is. I'd try either removing the line in the apache config that is looking for the LIBPHP4.SO library or installing PHP5 and making it look for the equivalent there.

---

### Post by iwegbue@gmail.com on 2007-08-22
Thanks for the reply. I finally figured that out. But whats happening now is the apache2 is not loading PHP pages altogether. When I click on the testphp.php page, the one that has phpinfo(), the browser asks to download the page instead of opening it. Could this have something to do with the document root? I though it was supposed to be in /var/www, which is where i have kept the testphp page.

---

