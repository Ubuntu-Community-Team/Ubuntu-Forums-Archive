---
title: "dpkg complains about a configuraton error"
date: 2008-03-23
forum: General Help
---

### Post by constchar* on 2008-03-23
Hey!
I've been trying to install mumble-server in my Ubuntu 7.10 Server Edition and I keep getting the
following results:

> 
**james@jpentium:~$ sudo dpkg -i mumble-server_1.1.3-0ubuntu1_i386.deb**
Selecting previously deselected package mumble-server.
(Reading database ... 43430 files and directories currently installed.)
Unpacking mumble-server (from mumble-server_1.1.3-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of mumble-server:
 mumble-server depends on libqt4-core (>= 4.3.2); however:
  Package libqt4-core is not installed.
 mumble-server depends on libqt4-sql (>= 4.3.2); however:
  Package libqt4-sql is not installed.
dpkg: error processing mumble-server (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mumble-server
**james@jpentium:~$ sudo apt-get install -f**
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglib2.0-0 libqt4-core libqt4-sql libsqlite0
Suggested packages:
  libqt4-dev
Recommended packages:
  libglib2.0-data
The following NEW packages will be installed:
  libglib2.0-0 libqt4-core libqt4-sql libsqlite0
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1907kB/2689kB of archives.
After unpacking 7549kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libqt4-core 4.3.2-0ubuntu3.2 [1769kB]
Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libqt4-sql 4.3.2-0ubuntu3.2 [139kB]
Fetched 1907kB in 36s (51.9kB/s)
Preconfiguring packages ...
Selecting previously deselected package libglib2.0-0.
(Reading database ... 43448 files and directories currently installed.)
Unpacking libglib2.0-0 (from .../libglib2.0-0_2.14.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-core.
Unpacking libqt4-core (from .../libqt4-core_4.3.2-0ubuntu3.2_i386.deb) ...
Selecting previously deselected package libsqlite0.
Unpacking libsqlite0 (from .../libsqlite0_2.8.17-2.1build1_i386.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4.3.2-0ubuntu3.2_i386.deb) ...
Setting up libglib2.0-0 (2.14.1-1ubuntu1) ...

Setting up libqt4-core (4.3.2-0ubuntu3.2) ...

Setting up libsqlite0 (2.8.17-2.1build1) ...

Setting up libqt4-sql (4.3.2-0ubuntu3.2) ...

Setting up mumble-server (1.1.3-0ubuntu1) ...
dpkg: error processing mumble-server (--configure):
 subprocess post-installation script returned error exit status 100
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 mumble-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can't seem to figure out why it is doing that and /var/log/dpkg.log doesn't tell me anything
more then what I see in the console.

Any ideas?

Thanks!

---

### Post by wolfen69 on 2008-03-23
give us the output of
```
cat /etc/apt/sources.list
```

---

### Post by constchar* on 2008-03-23
```

# 
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by wolfen69 on 2008-03-24
try uncommenting the lines with "gutsy partner" in them. then do- sudo apt-get update

---

### Post by zam1104 on 2008-04-12
I first had to apt-get install dbus

---

