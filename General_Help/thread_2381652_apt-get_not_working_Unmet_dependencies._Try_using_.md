---
title: "apt-get not working Unmet dependencies. Try using -f"
date: 2018-01-03
forum: General Help
---

### Post by bizhat on 2018-01-03
When i run apt update, i get following error, but it fail to resolve the  error,

```

root@ok-vm:~# apt update
Hit:1 http://azure.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://azure.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                                                              
Get:3 http://azure.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                                                                                      
Hit:4 http://software.virtualmin.com/vm/6/gpl/apt virtualmin-xenial InRelease                            
Get:5 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:6 http://software.virtualmin.com/vm/6/gpl/apt virtualmin-universal InRelease    
Ign:7 https://download.webmin.com/download/repository sarge InRelease
Hit:8 https://download.webmin.com/download/repository sarge Release
Fetched 306 kB in 2s (131 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
root@ok-vm:~# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.7 but it is not installed
E: Unmet dependencies. Try using -f.
root@ok-vm:~# 

```

I tried apt-get -f install as per said in the error message

```

root@ok-vm:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  mysql-server-5.7
Suggested packages:
  mailx tinyca
The following NEW packages will be installed:
  mysql-server-5.7
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
167 not fully installed or removed.
Need to get 0 B/2,708 kB of archives.
After this operation, 48.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
(Reading database ... 120876 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb ...
Aborting downgrade from (at least) 10.0 to 5.7.
If are sure you want to downgrade to 5.7, remove the file
/var/lib/mysql/debian-*.flag and try installing again.
dpkg: error processing archive /var/cache/apt/archives/mysql-server-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ok-vm:~# 

```


I don't need MySQL, its ok to remove it. This was caused by installing virtualmin ([https://www.virtualmin.com/](https://www.virtualmin.com/)) on Ubuntu 16.04


How i recover from this error. Now i can't do anything with apt.

---

### Post by Bashing-om on 2018-01-03
bizhat; Hummm ....

as we have:
> 
Aborting downgrade from (at least) 10.0 to 5.7.
If are sure you want to downgrade to 5.7, remove the file

and the current version in the 16.04 repo is "  5.7.20-0ubuntu0.16.04.1 "
we will want to know what is installed at this time to properly remove mysql.

Show us:
```

apt policy mysql*

```

Do we have pollution in one of it's many forms

---

### Post by bizhat on 2018-01-03
Thanks for the reply and finding it. I need to learn to read :)

Here is the result of the command

```

root@ok-vm:~# apt policy mysql*
mysqltcl:
  Installed: (none)
  Candidate: 3.052-1build1
  Version table:
     3.052-1build1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-mmm-agent:
  Installed: (none)
  Candidate: 2.2.1-1.1
  Version table:
     2.2.1-1.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-workbench:
  Installed: (none)
  Candidate: 6.3.6+dfsg-0ubuntu1
  Version table:
     6.3.6+dfsg-0ubuntu1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-client-5.5:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-client-5.6:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-client-5.7:
  Installed: 5.7.20-0ubuntu0.16.04.1
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
 *** 5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-mmm-tools:
  Installed: (none)
  Candidate: 2.2.1-1.1
  Version table:
     2.2.1-1.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-common-5.6:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-server-5.0:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-server-5.1:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-server-5.5:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-server-5.6:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-server-5.7:
  Installed: (none)
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
     5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-utilities:
  Installed: (none)
  Candidate: 1.6.1-2
  Version table:
     1.6.1-2 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-testsuite:
  Installed: (none)
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
     5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-mmm-common:
  Installed: (none)
  Candidate: 2.2.1-1.1
  Version table:
     2.2.1-1.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-server:
  Installed: 5.7.20-0ubuntu0.16.04.1
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
 *** 5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-client:
  Installed: 5.7.20-0ubuntu0.16.04.1
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
 *** 5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-sandbox:
  Installed: (none)
  Candidate: 3.1.04-1
  Version table:
     3.1.04-1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-client-core-5.5:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-client-core-5.6:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-client-core-5.7:
  Installed: 5.7.20-0ubuntu0.16.04.1
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
 *** 5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-testsuite-5.5:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-testsuite-5.6:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-testsuite-5.7:
  Installed: (none)
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
     5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-common:
  Installed: 5.7.20-0ubuntu0.16.04.1
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
 *** 5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-mmm-monitor:
  Installed: (none)
  Candidate: 2.2.1-1.1
  Version table:
     2.2.1-1.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysqltuner:
  Installed: (none)
  Candidate: 1.6.0-1
  Version table:
     1.6.0-1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-workbench-data:
  Installed: (none)
  Candidate: 6.3.6+dfsg-0ubuntu1
  Version table:
     6.3.6+dfsg-0ubuntu1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
mysql-server-core-5.1:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-server-core-5.5:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-server-core-5.6:
  Installed: (none)
  Candidate: (none)
  Version table:
mysql-server-core-5.7:
  Installed: 5.7.20-0ubuntu0.16.04.1
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
 *** 5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
mysql-source-5.7:
  Installed: (none)
  Candidate: 5.7.20-0ubuntu0.16.04.1
  Version table:
     5.7.20-0ubuntu0.16.04.1 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     5.7.11-0ubuntu6 500
        500 http://azure.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
root@ok-vm:~# 

```


I had mariadb before, not sure if that is why it saying downgrade, i already removed it.

```

root@ok-vm:~# dpkg -l | grep  mysql
iU  libdbd-mysql-perl                   4.033-1ubuntu0.1                           amd64        Perl5 database interface to the MySQL database
iU  libmysqlclient20:amd64              5.7.20-0ubuntu0.16.04.1                    amd64        MySQL database client library
iU  mysql-client                        5.7.20-0ubuntu0.16.04.1                    all          MySQL database client (metapackage depending on the latest version)
iU  mysql-client-5.7                    5.7.20-0ubuntu0.16.04.1                    amd64        MySQL database client binaries
iU  mysql-client-core-5.7               5.7.20-0ubuntu0.16.04.1                    amd64        MySQL database core client binaries
ii  mysql-common                        5.7.20-0ubuntu0.16.04.1                    all          MySQL database common files, e.g. /etc/mysql/my.cnf
iU  mysql-server                        5.7.20-0ubuntu0.16.04.1                    all          MySQL database server (metapackage depending on the latest version)
iU  mysql-server-core-5.7               5.7.20-0ubuntu0.16.04.1                    amd64        MySQL database server binaries
iU  php-mysql                           1:7.0+35ubuntu6                            all          MySQL module for PHP [default]
iU  php7.0-mysql                        7.0.22-0ubuntu0.16.04.1                    amd64        MySQL module for PHP
root@ok-vm:~# dpkg -l | grep maria
rc  mariadb-client-10.0                 10.0.31-0ubuntu0.16.04.2                   amd64        MariaDB database client binaries
rc  mariadb-common                      10.0.31-0ubuntu0.16.04.2                   all          MariaDB common metapackage
rc  mariadb-server-10.0                 10.0.31-0ubuntu0.16.04.2                   amd64        MariaDB database server binaries
root@ok-vm:~# 

```

---

### Post by Bashing-om on 2018-01-03
bizhat; Well,,,,

A deep web of dependencies ... not real sure of a best practice here to remove mysql .

We can try:
```

sudo apt purge mysql-client-5.7 mysql-client mysql-common mysql-server-5.7 mysql-server-core-5.7

```
Maybe I have the order correct ( apt depends <package> apt rdepends <package> ) and will be effective. 

Pending is php-mysql stuff .

[INDENT][INDENT]can not hurt to try
[/INDENT][/INDENT]

---

### Post by bizhat on 2018-01-03
Thanks, here is what i get when i try to uninstall, look like it won't allow me to uninstall with out installing mysql-server-5.7

```

root@ok-vm:~# apt purge mysql-client-5.7 mysql-client mysql-common mysql-server-5.7 mysql-server-core-5.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'mysql-server-5.7' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmysqlclient20 : Depends: mysql-common (>= 5.5) but it is not going to be installed
 mysql-server : Depends: mysql-server-5.7 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ok-vm:~# 

```

---

### Post by Bashing-om on 2018-01-03
bizhat; Ih Boy !

I won't say I am surprised .

Can we find a way forward with:
```

sudo apt purge mysql-common

```

[INDENT][INDENT]gotta be a way
[/INDENT][/INDENT]

---

### Post by bizhat on 2018-01-03
Thanks for the help, look like we are in a dead lock here :)

```

root@ok-vm:~# apt purge mysql-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmysqlclient20 : Depends: mysql-common (>= 5.5) but it is not going to be installed
 mysql-client-5.7 : Depends: mysql-common (>= 5.5) but it is not going to be installed
 mysql-server : Depends: mysql-server-5.7 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ok-vm:~# 

```


I tried there 2 commands too

```

root@ok-vm:~# apt purge -f libmysqlclient20
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libdbd-mysql-perl : Depends: libmysqlclient20 (>= 5.7.11) but it is not going to be installed
 mysql-server : Depends: mysql-server-5.7 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ok-vm:~# apt purge -f libmysqlclient20 libdbd-mysql-perl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-server : Depends: mysql-server-5.7 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@ok-vm:~# 

```

---

### Post by Bashing-om on 2018-01-04
bizhatbizhat; Yuk .

Looks like you are not the 1st to have this issue :)
Give this a whirl :
[https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1490071](https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1490071) post #12
it points back to :
[https://askubuntu.com/questions/789853/unable-to-install-or-remove-mysql](https://askubuntu.com/questions/789853/unable-to-install-or-remove-mysql)

[INDENT][INDENT]maybe, worth a shot
[/INDENT][/INDENT]

---

### Post by bizhat on 2018-01-04
Thanks  Bashing-om for the patience :)

Got it resolved my renaming /var/lib/mysql, after that apt install -f worked properly.

```

root@ok-vm:/var/lib# mv mysql mysql-old
root@ok-vm:/var/lib# apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  mysql-server-5.7
Suggested packages:
  mailx tinyca
The following NEW packages will be installed:
  mysql-server-5.7
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
167 not fully installed or removed.
Need to get 0 B/2,708 kB of archives.
After this operation, 48.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
(Reading database ... 120876 files and directories currently installed.)
Preparing to unpack .../mysql-server-5.7_5.7.20-0ubuntu0.16.04.1_amd64.deb ...
--snip---

```

---

### Post by Bashing-om on 2018-01-05
bizhat; Wonderful :)

Guess package manager got it's tail in a knot .

As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And onto our
[INDENT][INDENT]next adventure
[/INDENT][/INDENT]

---

