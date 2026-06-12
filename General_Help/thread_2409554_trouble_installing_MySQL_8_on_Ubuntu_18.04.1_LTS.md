---
title: "trouble installing MySQL 8 on Ubuntu 18.04.1 LTS"
date: 2019-01-03
forum: General Help
---

### Post by megunticook on 2019-01-03
I'm trying to install MySQL 8 on Ubuntu 18.04.1 LTS and failing. Not sure what exactly the problem is or how to fix it.

Here's the sequence I followed:

```
wget [https://dev.mysql.com/get/mysql-apt-config_0.8.11-1_all.deb](https://dev.mysql.com/get/mysql-apt-config_0.8.11-1_all.deb)
sudo dpkg -i mysql-apt-config_0.8.11-1_all.deb
sudo apt update
rm mysql-apt-config*
sudo apt install mysql-server
```

It presented me with the normal configuration screens and seemed like everything was fine.

But something went wrong because I can't start MySQL:

```
doctor@ED-Workstation:~$ sudo service mysql-server start
mysql-server: unrecognized service



```

I noticed Ubuntu reported some errors in the installation details (```
install: invalid user ‘mysql’
```) but can't figure out what exactly happened.

Here's the whole output from the installation attempt:

```
doctor@ED-Workstation:~$ sudo apt install mysql-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcgi-fast-perl libcgi-pm-perl libencode-locale-perl libevent-core-2.1-6 libfcgi-perl libfreetype6
  libhtml-parser-perl libhtml-tagset-perl libhtml-template-perl libhttp-date-perl libhttp-message-perl libio-html-perl
  liblwp-mediatypes-perl libtimedate-perl liburi-perl
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libmecab2 mecab-ipadic mecab-ipadic-utf8 mecab-utils mysql-client mysql-common mysql-community-client
  mysql-community-client-core mysql-community-server mysql-community-server-core
The following NEW packages will be installed:
  libmecab2 mecab-ipadic mecab-ipadic-utf8 mecab-utils mysql-client mysql-common mysql-community-client
  mysql-community-client-core mysql-community-server mysql-community-server-core mysql-server
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 57.1 MB of archives.
After this operation, 423 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu bionic/universe amd64 libmecab2 amd64 0.996-5 [257 kB]
Get:2 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 mysql-common amd64 8.0.13-1ubuntu18.04 [84.3 kB]
Get:3 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 mysql-community-client-core amd64 8.0.13-1ubuntu18.04 [1446 kB]
Get:4 http://archive.ubuntu.com/ubuntu bionic/universe amd64 mecab-utils amd64 0.996-5 [4856 B]
Get:5 http://archive.ubuntu.com/ubuntu bionic/universe amd64 mecab-ipadic all 2.7.0-20070801+main-1 [12.1 MB]
Get:6 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 mysql-community-client amd64 8.0.13-1ubuntu18.04 [2302 kB]Get:7 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 mysql-client amd64 8.0.13-1ubuntu18.04 [81.0 kB]
Get:8 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 mysql-community-server-core amd64 8.0.13-1ubuntu18.04 [17.3 MB]
Get:9 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 mysql-community-server amd64 8.0.13-1ubuntu18.04 [23.4 MB]Get:10 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 mysql-server amd64 8.0.13-1ubuntu18.04 [81.0 kB]
Get:11 http://archive.ubuntu.com/ubuntu bionic/universe amd64 mecab-ipadic-utf8 all 2.7.0-20070801+main-1 [3522 B]
Fetched 57.1 MB in 27s (2144 kB/s)
Preconfiguring packages ...
Selecting previously unselected package mysql-common.
(Reading database ... 29077 files and directories currently installed.)
Preparing to unpack .../00-mysql-common_8.0.13-1ubuntu18.04_amd64.deb ...
Unpacking mysql-common (8.0.13-1ubuntu18.04) ...
Selecting previously unselected package mysql-community-client-core.
Preparing to unpack .../01-mysql-community-client-core_8.0.13-1ubuntu18.04_amd64.deb ...
Unpacking mysql-community-client-core (8.0.13-1ubuntu18.04) ...
Selecting previously unselected package mysql-community-client.
Preparing to unpack .../02-mysql-community-client_8.0.13-1ubuntu18.04_amd64.deb ...
Unpacking mysql-community-client (8.0.13-1ubuntu18.04) ...
Selecting previously unselected package mysql-client.
Preparing to unpack .../03-mysql-client_8.0.13-1ubuntu18.04_amd64.deb ...
Unpacking mysql-client (8.0.13-1ubuntu18.04) ...
Selecting previously unselected package libmecab2:amd64.
Preparing to unpack .../04-libmecab2_0.996-5_amd64.deb ...
Unpacking libmecab2:amd64 (0.996-5) ...
Selecting previously unselected package mysql-community-server-core.
Preparing to unpack .../05-mysql-community-server-core_8.0.13-1ubuntu18.04_amd64.deb ...
Unpacking mysql-community-server-core (8.0.13-1ubuntu18.04) ...
Selecting previously unselected package mysql-community-server.
Preparing to unpack .../06-mysql-community-server_8.0.13-1ubuntu18.04_amd64.deb ...
install: invalid user ‘mysql’
dpkg: error processing archive /tmp/apt-dpkg-install-eoc1yw/06-mysql-community-server_8.0.13-1ubuntu18.04_amd64.deb (--unpack):
 new mysql-community-server package pre-installation script subprocess returned error exit status 1
Selecting previously unselected package mecab-utils.
Preparing to unpack .../07-mecab-utils_0.996-5_amd64.deb ...
Unpacking mecab-utils (0.996-5) ...
Selecting previously unselected package mecab-ipadic.
Preparing to unpack .../08-mecab-ipadic_2.7.0-20070801+main-1_all.deb ...
Unpacking mecab-ipadic (2.7.0-20070801+main-1) ...
Selecting previously unselected package mecab-ipadic-utf8.
Preparing to unpack .../09-mecab-ipadic-utf8_2.7.0-20070801+main-1_all.deb ...
Unpacking mecab-ipadic-utf8 (2.7.0-20070801+main-1) ...
Selecting previously unselected package mysql-server.
Preparing to unpack .../10-mysql-server_8.0.13-1ubuntu18.04_amd64.deb ...
Unpacking mysql-server (8.0.13-1ubuntu18.04) ...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-eoc1yw/06-mysql-community-server_8.0.13-1ubuntu18.04_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried to get more information this way:

```
doctor@ED-Workstation:~$ apt policy mysql-server
mysql-server:
  Installed: 8.0.13-1ubuntu18.04
  Candidate: 8.0.13-1ubuntu18.04
  Version table:
 *** 8.0.13-1ubuntu18.04 500
        500 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 Packages
        100 /var/lib/dpkg/status
     5.7.24-0ubuntu0.18.04.1 500
        500 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
     5.7.21-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages

```

Any advice appreciated. Been Googling around but just spinning my wheels here and getting nowhere.

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]megunticook[/COLOR]**]("https://ubuntuforums.org/member.php?u=2098716"),

Can you please try starting the mysql service using this command:

sudo service mysqld start

Regarding the error you got during install (install: invalid user &#8216;mysql&#8217;), this is because a user called mysql was not found on your system.

To fix this, please run the following commands:

1. sudo nano /etc/mysql/my.cnf
2. Change user = mysql to user = username of the user you want to run mysql from.
3. sudo nano /etc/init.d/mysql
4. Change test -e /var/run/mysqld || install -m 755 -o mysql -g root -d /var/run/mysqld to test -e /var/run/mysqld || install -m 755 -o Username consistent with running mysql above -g root -d /var/run/mysqld
5. sudo chown -R mysql run username /user/share/mysql

---

### Post by megunticook on 2019-01-03
Thanks for your quick response.

Results:

```
mysqld: unrecognized service
```
(I have NGINX installed not Apache)

There's no [COLOR=#000000]/etc/mysql/my.cnf file. Contents of /etc/mysql/ are:
[/COLOR]
```
doctor@ED-Workstation:/etc/mysql$ ls
conf.d  my.cnf.fallback.dpkg-new

```

Only line in my.conf.fallback.dpkg-new is "!includedir /etc/mysql/conf.d/"

```
doctor@ED-Workstation:/etc/mysql/conf.d$ ls
mysql.cnf.dpkg-new

```

Only line in that file is "[mysql]"

No mysql file in /etc/init.d/

```
doctor@ED-Workstation:/etc/init$ ls
php7.2-fpm.conf

```

I was able to get MySQL 8 installed on an identical Ubuntu installation. Only difference is here I had originally installed MySQL 5.7 (successfully), but I removed and purged it.

Here's a list of my repos: 

```
doctor@ED-Workstation:/etc/init$ apt policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 http://repo.mysql.com/apt/ubuntu bionic/mysql-tools amd64 Packages
     release o=MySQL,n=bionic,l=MySQL,c=mysql-tools,b=amd64
     origin repo.mysql.com
 500 http://repo.mysql.com/apt/ubuntu bionic/mysql-8.0 amd64 Packages
     release o=MySQL,n=bionic,l=MySQL,c=mysql-8.0,b=amd64
     origin repo.mysql.com
 500 http://repo.mysql.com/apt/ubuntu bionic/mysql-apt-config amd64 Packages
     release o=MySQL,n=bionic,l=MySQL,c=mysql-apt-config,b=amd64
     origin repo.mysql.com
 500 http://mirror.lstn.net/mariadb/repo/10.3/ubuntu bionic/main arm64 Packages
     release o=MariaDB,n=bionic,l=MariaDB,c=main,b=arm64
     origin mirror.lstn.net
 500 http://mirror.lstn.net/mariadb/repo/10.3/ubuntu bionic/main ppc64el Packages
     release o=MariaDB,n=bionic,l=MariaDB,c=main,b=ppc64el
     origin mirror.lstn.net
 500 http://mirror.lstn.net/mariadb/repo/10.3/ubuntu bionic/main amd64 Packages
     release o=MariaDB,n=bionic,l=MariaDB,c=main,b=amd64
     origin mirror.lstn.net
 500 http://nginx.org/packages/ubuntu bionic/nginx amd64 Packages
     release o=nginx,a=stable,n=bionic,l=nginx,c=nginx,b=amd64
     origin nginx.org
 500 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic-security,n=bionic,l=Ubuntu,c=multiverse,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic-security,n=bionic,l=Ubuntu,c=universe,b=amd64
     origin security.ubuntu.com
 500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic-security,n=bionic,l=Ubuntu,c=main,b=amd64
     origin security.ubuntu.com
 100 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic-backports,n=bionic,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic-updates,n=bionic,l=Ubuntu,c=multiverse,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic-updates,n=bionic,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic-updates,n=bionic,l=Ubuntu,c=restricted,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic-updates,n=bionic,l=Ubuntu,c=main,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic,n=bionic,l=Ubuntu,c=multiverse,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic,n=bionic,l=Ubuntu,c=universe,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic,n=bionic,l=Ubuntu,c=restricted,b=amd64
     origin archive.ubuntu.com
 500 http://archive.ubuntu.com/ubuntu bionic/main amd64 Packages
     release v=18.04,o=Ubuntu,a=bionic,n=bionic,l=Ubuntu,c=main,b=amd64
     origin archive.ubuntu.com
Pinned packages:

```

Just for kicks I tried installing MariaDB, that didn't work either:

```
doctor@ED-Workstation:/etc/init$ sudo apt install mariadb-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 mariadb-server : Depends: mariadb-server-10.3 (>= 1:10.3.11+maria~bionic) but it is not going to be installed
 mysql-server : Depends: mysql-community-server (= 8.0.13-1ubuntu18.04) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
doctor@ED-Workstation:/etc/init$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcgi-fast-perl libcgi-pm-perl libencode-locale-perl libevent-core-2.1-6 libfcgi-perl libfreetype6 libhtml-parser-perl libhtml-tagset-perl
  libhtml-template-perl libhttp-date-perl libhttp-message-perl libio-html-perl liblwp-mediatypes-perl libtimedate-perl liburi-perl
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  mysql-community-server
The following NEW packages will be installed:
  mysql-community-server
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
10 not fully installed or removed.
Need to get 0 B/23.4 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 29350 files and directories currently installed.)
Preparing to unpack .../mysql-community-server_8.0.13-1ubuntu18.04_amd64.deb ...
install: invalid user ‘mysql’
dpkg: error processing archive /var/cache/apt/archives/mysql-community-server_8.0.13-1ubuntu18.04_amd64.deb (--unpack):
 new mysql-community-server package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-community-server_8.0.13-1ubuntu18.04_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Seems like Ubuntu isn't liking this user named 'mysql'

What do I do about this? Haven't run into this before and not finding an answer through Google...

---

### Post by clementc on 2019-01-04
Hi [**[COLOR=#000000]megunticook[/COLOR]**]("https://ubuntuforums.org/member.php?u=2098716"),

I will have to leave a more knowledgeable user answer your questions I am afraid.

I don't know if this is possible, but maybe reinstalling MySQL 5.7 before updating to v8 might help.

---

### Post by megunticook on 2019-01-04
After way too many hours of head-banging, I finally just started with a clean slate and did a fresh Ubuntu install, followed by NGINX and MySQL 8. The installation seemed to go fine. But I can't start MySQL. What am I doing wrong?

```
doctor@ED-Workstation:~$ sudo service mysql start
mysql: unrecognized service
doctor@ED-Workstation:~$ sudo service mysql-server start
mysql-server: unrecognized service
doctor@ED-Workstation:~$
```

---

### Post by clementc on 2019-01-05
[COLOR=#000000]Hi [/COLOR][**[COLOR=#000000]megunticook[/COLOR]**]("https://ubuntuforums.org/member.php?u=2098716")[COLOR=#000000],[/COLOR]

[COLOR=#000000]Can you please try starting the mysql service using this command:[/COLOR]

[COLOR=#000000]sudo service mysqld start[/COLOR]

---

