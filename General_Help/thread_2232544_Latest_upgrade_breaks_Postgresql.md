---
title: "Latest upgrade breaks Postgresql"
date: 2014-07-02
forum: General Help
---

### Post by Joel_Hershberger on 2014-07-02
I am running Ubuntu 12.04 LTS and just recently did an apt-get upgrade to support some packages I needed. This apparently broke postgresql-9.1. It tells me to run "apt-get -f install" to fix it but no luck. Following is the error I receive:

```
Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libkms1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  postgresql-9.1 postgresql-contrib-9.1
Suggested packages:
  oidentd ident-server locales-all libdbd-pg-perl
The following packages will be upgraded:
  postgresql-9.1 postgresql-contrib-9.1
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,624 kB of archives.
After this operation, 350 kB disk space will be freed.
Do you want to continue [Y/n]? dpkg: dependency problems prevent configuration of postgresql-9.1:
 postgresql-client-9.1 (9.1.13-1.pgdg12.4+1) breaks postgresql-9.1 (<< 9.1.13-1.pgdg12.4+1) and is installed.
  Version of postgresql-9.1 to be configured is 9.1.11-1.pgdg12.4+1.
dpkg: error processing postgresql-9.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-contrib-9.1:
 postgresql-contrib-9.1 depends on postgresql-9.1 (= 9.1.12-0ubuntu0.12.04); however:
  Version of postgresql-9.1 on system is 9.1.11-1.pgdg12.4+1.
dpkg: error processing postgresql-contrib-9.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postgresql-9.1-plv8:
 postgresql-9.1-plv8 depends on postgresql-9.1; however:
  Package postgresql-9.1 is not configured yet.
dpkg: error processing postgresql-9.1-plv8 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-9.1
 postgresql-contrib-9.1
 postgresql-9.1-plv8


```

I've tried everything I know to fix this. This is running our ERP system so it's pretty urgent. For some stupid reason I only made a database backup before doing this and did not make a complete system backup.

Any ideas?

---

### Post by bapoumba on 2014-07-02
[http://packages.ubuntu.com/precise/postgresql-9.1](http://packages.ubuntu.com/precise/postgresql-9.1) > postgresql-9.1 (9.1.12-0ubuntu0.12.04) 
[http://packages.ubuntu.com/precise/postgresql-client-9.1](http://packages.ubuntu.com/precise/postgresql-client-9.1) > postgresql-client-9.1 (9.1.12-0ubuntu0.12.04) 
```
postgresql-client-9.1 (9.1.13-1.pgdg12.4+1) breaks postgresql-9.1 (<< 9.1.13-1.pgdg12.4+1) and is installed.
  Version of postgresql-9.1 to be configured is 9.1.11-1.pgdg12.4+1.
```
Any ppa or third party repo you may have these coming from ?

---

### Post by Joel_Hershberger on 2014-07-02
I just checked sources.list and that is completely stock. It may have come from a github repo though. Any way I can roll it back to an older version?

---

### Post by bapoumba on 2014-07-03
You could always uninstall postgresql and reinstall it if you are confident your sources are ubuntu only. Just to make sure, what are the outputs to :
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by Joel_Hershberger on 2014-07-03
source.list:

```


# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted

#deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main


```


ls -l /etc/apt/sources.list.d:
```

total 4
-rw-r--r-- 1 root root 63 Feb 27 08:27 pgdg.list

```


tail -v -n +1 /etc/apt/sources.list.d/*:
```

==> /etc/apt/sources.list.d/pgdg.list <==
deb http://apt.postgresql.org/pub/repos/apt/ precise-pgdg main

```

The way the pgdg.list file looks it appears as if it is getting it from another repository as well. Am I ok to just remove this repo?

---

### Post by Joel_Hershberger on 2014-07-05
I commented out this repo and then ran apt-get -f install. This uninstalled postgresql. After a reinstall of postgres that part seemed to work.

---

### Post by bapoumba on 2014-07-05
Oh thanks, sorry I missed your previous reply.. Please mark your thread as solved (under Thread tools) :)

---

