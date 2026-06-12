---
title: "phpMyadmin"
date: 2006-12-20
forum: General Help
---

### Post by drito on 2006-12-20
I have installed Apache2, PHP... with no problems whatsoever. When I tried to install phpMyadmin:

```
sudo aptitude update && sudo aptitude install phpmyadmin
```

I got:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not get lock /var/lib/aptitude/lock - open (11 Resource temporarily unavailable)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Get:2 http://ba.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://ba.archive.ubuntu.com edgy/main Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://ba.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://ba.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://ba.archive.ubuntu.com edgy/multiverse Translation-en_US
Get:3 http://ba.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://ba.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://ba.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://ba.archive.ubuntu.com edgy Release
Hit http://ba.archive.ubuntu.com edgy-updates Release
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://ba.archive.ubuntu.com edgy/main Packages
Hit http://ba.archive.ubuntu.com edgy/restricted Packages
Hit http://ba.archive.ubuntu.com edgy/main Sources
Hit http://ba.archive.ubuntu.com edgy/restricted Sources
Hit http://ba.archive.ubuntu.com edgy/universe Packages
Hit http://ba.archive.ubuntu.com edgy/multiverse Packages
Hit http://ba.archive.ubuntu.com edgy/universe Sources
Hit http://ba.archive.ubuntu.com edgy/multiverse Sources
Hit http://ba.archive.ubuntu.com edgy-updates/main Packages
Hit http://ba.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://ba.archive.ubuntu.com edgy-updates/main Sources
Hit http://ba.archive.ubuntu.com edgy-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not get lock /var/lib/aptitude/lock - open (11 Resource temporarily unavailable)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  phpmyadmin
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3607kB of archives. After unpacking 14.1MB will be used.
Do you want to continue? [Y/n/?] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
(Reading database ...
dpkg: serious warning: files list file for package `phpmyadmin' missing, assuming package has no files currently installed.
95328 files and directories currently installed.)
Preparing to replace phpmyadmin 4:2.8.2-0.2 (using .../phpmyadmin_4%3a2.8.2-0.2_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing /var/cache/apt/archives/phpmyadmin_4%3a2.8.2-0.2_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/phpmyadmin_4%3a2.8.2-0.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up php5-cgi (5.1.6-1ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing php5-cgi (--configure):
 subprocess post-installation script returned error exit status 1
Setting up php5-gd (5.1.6-1ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing php5-gd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up php5-mcrypt (5.1.2-1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing php5-mcrypt (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 php5-cgi
 php5-gd
 php5-mcrypt

```

(Universe and multiverse repos are enabled). Any help?

---

### Post by darrenm on 2006-12-20
> **drito said:**
> I have installed Apache2, PHP... with no problems whatsoever. When I tried to install phpMyadmin:

```
sudo aptitude update && sudo aptitude install phpmyadmin
```

I got:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not get lock /var/lib/aptitude/lock - open (11 Resource temporarily unavailable)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Get:2 http://ba.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://ba.archive.ubuntu.com edgy/main Translation-en_US
Hit http://security.ubuntu.com edgy-security Release
Ign http://ba.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://ba.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://ba.archive.ubuntu.com edgy/multiverse Translation-en_US
Get:3 http://ba.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://ba.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://ba.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://ba.archive.ubuntu.com edgy Release
Hit http://ba.archive.ubuntu.com edgy-updates Release
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://ba.archive.ubuntu.com edgy/main Packages
Hit http://ba.archive.ubuntu.com edgy/restricted Packages
Hit http://ba.archive.ubuntu.com edgy/main Sources
Hit http://ba.archive.ubuntu.com edgy/restricted Sources
Hit http://ba.archive.ubuntu.com edgy/universe Packages
Hit http://ba.archive.ubuntu.com edgy/multiverse Packages
Hit http://ba.archive.ubuntu.com edgy/universe Sources
Hit http://ba.archive.ubuntu.com edgy/multiverse Sources
Hit http://ba.archive.ubuntu.com edgy-updates/main Packages
Hit http://ba.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://ba.archive.ubuntu.com edgy-updates/main Sources
Hit http://ba.archive.ubuntu.com edgy-updates/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Could not get lock /var/lib/aptitude/lock - open (11 Resource temporarily unavailable)
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  phpmyadmin
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3607kB of archives. After unpacking 14.1MB will be used.
Do you want to continue? [Y/n/?] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
(Reading database ...
dpkg: serious warning: files list file for package `phpmyadmin' missing, assuming package has no files currently installed.
95328 files and directories currently installed.)
Preparing to replace phpmyadmin 4:2.8.2-0.2 (using .../phpmyadmin_4%3a2.8.2-0.2_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing /var/cache/apt/archives/phpmyadmin_4%3a2.8.2-0.2_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/phpmyadmin_4%3a2.8.2-0.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up php5-cgi (5.1.6-1ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing php5-cgi (--configure):
 subprocess post-installation script returned error exit status 1
Setting up php5-gd (5.1.6-1ubuntu2.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing php5-gd (--configure):
 subprocess post-installation script returned error exit status 1
Setting up php5-mcrypt (5.1.2-1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process
dpkg: error processing php5-mcrypt (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 php5-cgi
 php5-gd
 php5-mcrypt

```

(Universe and multiverse repos are enabled). Any help?

Something else is using APT. You could manually kill anything by doing
```
ps -ef | grep apt
``` and killing anything like synaptic etc 

or just reboot. :)

---

### Post by drito on 2006-12-20
I have done it allready, but nothing has changed!?

---

### Post by drito on 2006-12-20
I have managed to install phpmyadmin but now I am having problems with mysql. I tried to reinstall mysql and I got this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
mysql is not currently installed, so it will not be reinstalled.
The following packages are BROKEN:
  mailx
The following packages are unused and will be REMOVED:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0
The following packages have been kept back:
  mysql-server-5.0
0 packages upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 19.1MB will be freed.
The following packages have unmet dependencies:
  mailx: Depends: postfix but it is not installable or
                  mail-transport-agent which is a virtual package.
Resolving dependencies...
E: I wasn't able to locate a file for the mysql-server-5.0 package. This might mean you need to manually fix this package. (due to missing arch)
The following actions will resolve these dependencies:

Install the following packages:
postfix [2.3.3-1 (edgy)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl
  mysql-client-5.0
The following NEW packages will be automatically installed:
  postfix
The following packages have been kept back:
  mysql-server-5.0
The following NEW packages will be installed:
  postfix
0 packages upgraded, 1 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B/1067kB of archives. After unpacking 16.6MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the mysql-server-5.0 package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
```

What to do?

---

