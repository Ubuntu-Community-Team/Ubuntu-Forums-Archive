---
title: "Package Catalog Broken for mysql-server"
date: 2014-01-31
forum: General Help
---

### Post by salmndr on 2014-01-31
Hello All,
Updated manager updated my system, and as a result the package manager is broken. I have taken a number of steps as I found them in the forum, but none has worked.
This is the copy of the error that I get. Any help will be greatly appreciated.
Thanks

Salmndr

dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 mysql-server-5.5
 mysql-server

---

### Post by Bashing-om on 2014-01-31
salmndr; Hi ! Welcome to the forum .

What results if you heed the package manager's advise ?
```

sudo dpkg-reconfigure  mysql-server

```
If that does not resolve the problem perhaps will yield additional info to follow up.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by salmndr on 2014-01-31
> **Bashing-om said:**
> salmndr; Hi ! Welcome to the forum .

What results if you heed the package manager's advise ?
```

sudo dpkg-reconfigure  mysql-server

```
If that does not resolve the problem perhaps will yield additional info to follow up.
[INDENT][INDENT]just try'n to help
[/INDENT]
[/INDENT]


This the result I got
/usr/sbin/dpkg-reconfigure: mysql-server is broken or not fully installed

I have used sudo apt-get install -f and the reply is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-53 linux-headers-3.2.0-49
  linux-headers-3.2.0-53-generic-pae linux-headers-3.2.0-49-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mysql-server mysql-server-5.5
Suggested packages:
  tinyca
The following packages will be upgraded:
  mysql-server mysql-server-5.5
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/8,735 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: dependency problems prevent configuration of mysql-server-5.5:
 mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.35-0ubuntu0.12.04.1); however:
  Version of mysql-server-core-5.5 on system is 5.5.35-0ubuntu0.12.04.2.
dpkg: error processing mysql-server-5.5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.5; however:
  Package mysql-server-5.5 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mysql-server-5.5
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help will be greatly appreciated.
Salmndr

---

### Post by Bashing-om on 2014-01-31
salmndr; Well.

This:
> 
mysql-server-5.5 depends on mysql-server-core-5.5 (= 5.5.35-0ubuntu0.12.04.1); however:
Version of mysql-server-core-5.5 on system is 5.5.35-0ubuntu0.12.04.2.
 seems to indicate that you have a version of mysql-server that is a later version than is in the repository.
Are you prepared to remove mysql-server and try and re-install ?
Post back the output of terminal codes: Between code tags to maintain readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

lsb_release -a
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
Just to verify what we are working with and where we are heading into.

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by salmndr on 2014-02-01
This is what I get when I run the three commands
> 
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

cat /etc/apt/sources.list.d/*.list
cat: /etc/apt/sources.list.d/*.list: No such file or directory






---

### Post by Bashing-om on 2014-02-01
salmndr; Well, well (?),

I do not see a source for "mysql-server", How did you initially install it ?
Getting a bit out of my depth here with a application installed through other means, but, will try and struggle through this together.

Let's look at what we are working with.
Post back the outputs of terminal codes:
```

apt-cache policy mysql-server
apt-cache policy mysql-server-core

```

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by salmndr on 2014-02-01
I had installed lamp-server through
Code:
> 
sudo apt-get install tasksel
and:
sudo tasksel install lamp-server

This installation was done over six months ago, and I had not had any problems with it. Only a few days ago I logged to my ubuntu machine and saw there were updates available, so I updated the system. And then the problems started. i must say that i tried to uninstall mysql-server and its dependecies after failing to resolve this issue, but it did not resolve the problems with package manager.
Here are the results of the two commands that you mentioned

> 
apt-cache policy mysql-server
mysql-server:
  Installed: 5.5.35-0ubuntu0.12.04.1
  Candidate: 5.5.35-0ubuntu0.12.04.2
  Version table:
     5.5.35-0ubuntu0.12.04.2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
 *** 5.5.35-0ubuntu0.12.04.1 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
        100 /var/lib/dpkg/status
apt-cache policy mysql-server-core
mysql-server-core:
  Installed: (none)
  Candidate: (none)
  Version table:


     5.5.22-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages




---

### Post by Bashing-om on 2014-02-01
salmndr; OK,

That it is a base install means something really stinks. 

> 
Version of mysql-server-core-5.5 on system is 5.5.35-0ubuntu0.12.04.2.

But !
> 
apt-cache policy mysql-server-core
mysql-server-core:
Installed: (none)
Candidate: (none)


Let's see what the system says when we try to install the mysterious "mysql-server-core".
```

sudo apt-get install mysql-server-core

```

[INDENT][INDENT]what we have here is
[INDENT][INDENT]a failure to communicate
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by salmndr on 2014-02-01
[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508") , since my ubuntu pc is not a production machine and does not have any files that I needed, I took the path of least resistance and installed a fresh ubuntu OS.
So far so good.
Thanks for all your help.

---

### Post by Bashing-om on 2014-02-01
salmndr; Hey ,

Not at all a problem. (re-)install is one sure fire fix that works each and every time- though we learn nothing from doing so.
There are those times for a variety of reasons that (RE-)installing is the thing to do.

Please mark this thread as solved, as an aid to keep the forum tidy.

[INDENT]The NucleaR approach
[INDENT][INDENT]works
[/INDENT][/INDENT][/INDENT]

---

### Post by askvictor on 2014-04-02
I have the same problem; seems a little rich to mark it as solved when the 'solution' was a re-install.

---

### Post by askvictor on 2014-04-02
Right - I've managed to fix it by downloading the deb of mysql-server-core 5.5.35-0ubuntu0.12.04.1 and installing that using dpkg. After this an apt-get -f install got things working again.
A subsequent apt-get update and apt-get upgrade then got everything up to 12.04.02.

---

