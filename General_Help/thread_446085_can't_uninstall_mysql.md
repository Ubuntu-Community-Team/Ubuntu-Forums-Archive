---
title: "can't uninstall mysql"
date: 2007-05-16
forum: General Help
---

### Post by chris.olsen on 2007-05-16
On the new ubuntu setup I was starting up a new ROR project, when it seemed that I didn't have mysql installed yet.  So I tried to install it, but it failed since my internet connection went out.  Now I can't seem to get it installed at all.

I tried to remove it with aptitude remove ..., but that failed as well.  It seems that it is looking for mysql-server-5.0, so I tried installing it with aptitude install mysql-server-5.0 but that fails in the same way.

Not sure how to fix this.

This is what I get
=====================================
```

chris@ubuntu:$ sudo aptitude install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be installed:
  mysql-server 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/47.5kB of archives. After unpacking 86.0kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  mysql-server 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
Selecting previously deselected package mysql-server.
(Reading database ... 120998 files and directories currently installed.)
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1_all.deb) ...
 * Stopping MySQL database server mysqld                                             [ OK ] 
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                             [ OK ] 
 * Starting MySQL database server mysqld                                             [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                             [ OK ] 
 * Starting MySQL database server mysqld                                             [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server

```

---

### Post by heimo on 2007-05-16
First thing I'd try is --purge removing it. **Warning** removes all myslq-related files. May even remove databases, I'm not sure.
```
sudo aptitude --purge remove mysql-server-5.0 mysql-server
```

---

### Post by chris.olsen on 2007-05-16
I am not sure if the purge option worked, since it didn't seem to re-download them, that is if the purge means clear all the previous libraries from the computer

This is what I got

```

chris@ubuntu:$ sudo aptitude --purge remove mysql-server-5.0 mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  libdbd-mysql-perl{p} libdbi-perl{p} libnet-daemon-perl{p} libplrpc-perl{p} 
  mysql-client-5.0{p} 
The following packages will be REMOVED:
  mysql-server mysql-server-5.0 
0 packages upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 89.5MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 120999 files and directories currently installed.)
Removing mysql-server ...
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                             [ OK ] 
(Reading database ... 119414 files and directories currently installed.)
Removing mysql-client-5.0 ...
Removing libdbd-mysql-perl ...
Removing libdbi-perl ...
Removing libplrpc-perl ...
Removing libnet-daemon-perl ...
chris@ubuntu:~/rails_apps/thingstotrack$ sudo aptitude install mysql-server-5.0Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client-5.0 
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client-5.0 
  mysql-server-5.0 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/34.0MB of archives. After unpacking 89.4MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  libnet-daemon-perl libdbi-perl libdbd-mysql-perl mysql-client-5.0 libplrpc-perl 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 119224 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.53-1build1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0008-1build1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.38-0ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.38-0ubuntu1_i386.deb) ...
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.53-1build1) ...
Setting up libdbd-mysql-perl (3.0008-1build1) ...
Setting up mysql-client-5.0 (5.0.38-0ubuntu1) ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                             [ OK ] 
 * Starting MySQL database server mysqld                                             [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                             [ OK ] 
 * Starting MySQL database server mysqld                                             [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0

```

---

### Post by heimo on 2007-05-16
```
WARNING: untrusted versions of the following packages will be installed!
```

What repositories are you using? (/etc/apt/sources.lst)

---

### Post by dannyboy79 on 2007-05-16
i think you may have something more to worry about that not being able to uninstall mysql server. why in the world are you getting the untrusted content warning??? what does your /etc/apt/sources.list look like? mysql is in the universe or mutliverse repo I thought so you shouldn't be gettintg that warning I wouldn't think. anytime you add other people's repo's which aren't trusted by ubuntu you could possibly get virus's, backdoors, trojans, and the like on your comptuer. I'd be interested in seeing what this returns

netstat -pant

this shows all your open ports and also if anyone is connected to you. just an fyi, it will show a few hostnames or ip's connected to you since you're on the internet but I just can't understand why mysql would be giving you that error and expecially now that you're having problems removing it.

---

### Post by chris.olsen on 2007-05-16
Here is my sources.list content.  I can't see anything on there that would be considered bad...

```

# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
## The Following is for Beryl
deb http://ubuntu.beryl-project.org/ feisty main

```

here is the net stat output
```

chris@ubuntu:~/rails_apps/thingstotrack$ netstat -pant
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN     5691/Xgl            
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     -                   
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     -                   
tcp        0      0 192.168.1.148:38958     207.46.27.177:1863      ESTABLISHED5909/kopete         
tcp        0      0 192.168.1.148:41447     209.85.167.147:80       ESTABLISHED9256/firefox-bin    
tcp        0      0 192.168.1.148:42382     207.46.111.39:1863      ESTABLISHED5909/kopete         
tcp        0      0 192.168.1.148:38539     207.46.26.28:1863       ESTABLISHED5909/kopete         
tcp        0      0 192.168.1.148:54494     207.46.26.87:1863       ESTABLISHED5909/kopete         
tcp6       0      0 :::6001                 :::*                    LISTEN     5691/Xgl  

```

other than leaching internet off my neighbors all is ok, well except for the mysql issues.

Thanks for the help

---

### Post by chris.olsen on 2007-05-16
I was finally able to remove it after running 
apt-get remove mysql-server mysql-server-5.0
aptitude remove mysql-server mysql-server-5.0

not sure if I had to run them both but after that running the "mysql" command resulted in a command not found error.

I am still unable to install it, it keeps failing when trying to start the database-server

---

### Post by chris.olsen on 2007-05-16
it seems that the aptitude command is responsible for the untrusted content warnings.  I am not sure if this is reason enough not to use it or not though.

---

### Post by chris.olsen on 2007-05-16
maybe I was wrong about that.  It seemed to be so for another program that I was installing.  

Here is the output from the apt-get command

```

chris@ubuntu:~$ sudo apt-get install mysql-server mysql-client
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0 mysql-server-5.0
Suggested packages:
  dbishell libcompress-zlib-perl tinyca
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl mysql-client
  mysql-client-5.0 mysql-server mysql-server-5.0
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 45.4kB/34.1MB of archives.
After unpacking 89.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libnet-daemon-perl libplrpc-perl libdbi-perl libdbd-mysql-perl
  mysql-client-5.0 mysql-server-5.0 mysql-client mysql-server
Install these packages without verification [y/N]? y
Get:1 http://us.archive.ubuntu.com feisty/main mysql-client 5.0.38-0ubuntu1 [45.4kB]
Fetched 45.4kB in 1s (39.0kB/s)      
Preconfiguring packages ...
Selecting previously deselected package libnet-daemon-perl.
(Reading database ... 119950 files and directories currently installed.)
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.38-1.1_all.deb) ...
Selecting previously deselected package libplrpc-perl.
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2017-1.1_all.deb) ...
Selecting previously deselected package libdbi-perl.
Unpacking libdbi-perl (from .../libdbi-perl_1.53-1build1_i386.deb) ...
Selecting previously deselected package libdbd-mysql-perl.
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0008-1build1_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.38-0ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.38-0ubuntu1_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.38-0ubuntu1_all.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.38-0ubuntu1_all.deb) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
Setting up libnet-daemon-perl (0.38-1.1) ...
Setting up libplrpc-perl (0.2017-1.1) ...
Setting up libdbi-perl (1.53-1build1) ...
Setting up libdbd-mysql-perl (3.0008-1build1) ...
Setting up mysql-client-5.0 (5.0.38-0ubuntu1) ...
Setting up mysql-server-5.0 (5.0.38-0ubuntu1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mysql-client (5.0.38-0ubuntu1) ...
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dannyboy79 on 2007-05-17
you may want to look around as to why mysql is stating that it's untrusted or that all that software can't be authenticated. your sources.list looks fine and the only thing that's listening on your computer is port 6001 which I notice has XGL in it's description so I am not sure what that's all about, are you using XVNC? if you don't think so than this is something to be concerned about!!!

---

### Post by chris.olsen on 2007-05-17
when I boot up, I use the gnome / XGL session to get the beryl3D effects.

---

### Post by uberdog on 2008-04-16
Removing /etc/mysql prior to uninstalling worked for me.

---

