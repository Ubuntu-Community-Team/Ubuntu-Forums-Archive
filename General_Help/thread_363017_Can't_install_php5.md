---
title: "Can't install php5?"
date: 2007-02-16
forum: General Help
---

### Post by erikcw on 2007-02-16
Hi all,

I'm trying to install apache2 and php5 on my Edgy machine.  When I try to install php5 I get this error:

> 
erik@turbo:/tmp$ sudo aptitude install php5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
erik@turbo:/tmp$ sudo aptitude install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  thttpd
The following NEW packages will be installed:
  libapache2-mod-php5 php5 php5-common
0 packages upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 139kB/2458kB of archives. After unpacking 5444kB will be used.
Do you want to continue? [Y/n/?]
Writing extended state information... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main php5-common 5.1.6-1ubuntu2.1 [139kB]
Fetched 139kB in 1s (78.3kB/s)
(Reading database ... 182300 files and directories currently installed.)
Removing thttpd ...
Stopping web server: kill: 60: No such process

dpkg: error processing thttpd (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 thttpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
erik@turbo:/tmp$ php5
bash: php5: command not found
erik@turbo:/tmp$ sudo aptitude remove thttpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  thttpd
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 221kB will be freed.
Writing extended state information... Done
(Reading database ... 182300 files and directories currently installed.)
Removing thttpd ...
Stopping web server: kill: 60: No such process

dpkg: error processing thttpd (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 thttpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
erik@turbo:/tmp$


How do I figure out what install thttpd and how to remove it or install php5 along side it?

Thanks!

---

### Post by der_joachim on 2007-02-16
I have this issue occasionally as well. Apparently there's a scheduled job that automatically does an apt-get update. For some reason that takes quite a lot of time. You can either wait for it to be over or kill the process.

---

### Post by llamakc on 2007-02-16
Have you tried `sudo apt-get -f install` yet?

---

### Post by erikcw on 2007-02-16
I tried apt-get -f install php5 - it appears to install without any errors that way.  But I can't find the binary anywhere.  which php (or php5) gives me nothing.  locate php5 gives a bunch of docs and configuration files, but no binary.

> 
erik@turbo:/tmp$ sudo apt-get -f install php5
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libapache2-mod-php5 php5-common
Suggested packages:
  php-pear
The following NEW packages will be installed:
  libapache2-mod-php5 php5 php5-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2458kB of archives.
After unpacking 5665kB of additional disk space will be used.
Do you want to continue [Y/n]?
Selecting previously deselected package php5-common.
(Reading database ... 182302 files and directories currently installed.)
Unpacking php5-common (from .../php5-common_5.1.6-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.1.6-1ubuntu2.1_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.1.6-1ubuntu2.1_all.deb) ...
Setting up php5-common (5.1.6-1ubuntu2.1) ...
Setting up libapache2-mod-php5 (5.1.6-1ubuntu2.1) ...

Setting up php5 (5.1.6-1ubuntu2.1) ...
erik@turbo:/tmp$ php
bash: php: command not found
erik@turbo:/tmp$ which php
erik@turbo:/tmp$ php5
bash: php5: command not found
erik@turbo:/tmp$ which php5
erik@turbo:/tmp$ locate php5
/var/cache/apt/archives/php5_5.1.6-1ubuntu2.1_all.deb
/var/cache/apt/archives/php5-curl_5.1.6-1ubuntu2.1_i386.deb
/var/cache/apt/archives/libapache2-mod-php5_5.1.6-1ubuntu2.1_i386.deb
/var/lib/dpkg/info/php5.list
/var/lib/dpkg/info/libapache2-mod-php5.list
/var/lib/dpkg/info/php5-common.postrm
/var/lib/dpkg/info/php5-common.list
/var/lib/dpkg/info/php5-common.conffiles
/var/lib/dpkg/info/php5-common.md5sums
/var/lib/dpkg/info/php5-mysqli.list
/var/lib/dpkg/info/php5-mysqli.postrm
/var/lib/dpkg/info/php5-mysql.list
/var/lib/dpkg/info/php5-mysql.postrm
/var/lib/dpkg/info/libapache2-mod-php5.postrm
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.prerm
/var/lib/dpkg/info/libapache2-mod-php5.md5sums
/var/lib/dpkg/info/libapache2-mod-php5.conffiles
/var/lib/dpkg/info/php5-cli.list
/var/lib/dpkg/info/php5-cli.postrm
/var/lib/dpkg/info/php5-curl.list
/var/lib/dpkg/info/php5-curl.postrm
/var/lib/php5
/etc/cron.d/php5
/etc/apache2/mods-available/php5.conf
/etc/apache2/mods-available/php5.load
/etc/php5
/etc/php5/apache2
/etc/php5/apache2/php.ini
/etc/php5/cli
/etc/php5/cli/php.ini
/usr/lib/apache2/modules/libphp5.so
/usr/lib/php5
/usr/lib/php5/maxlifetime
/usr/lib/php5/libexec
/usr/lib/php5/20051025
/usr/share/doc/php5
/usr/share/doc/libapache2-mod-php5
/usr/share/doc/php5-common
/usr/share/doc/php5-common/README.CVS-RULES.gz
/usr/share/doc/php5-common/examples
/usr/share/doc/php5-common/examples/php.ini-recommended
/usr/share/doc/php5-common/examples/php.ini-paranoid
/usr/share/doc/php5-common/examples/php.ini-dist
/usr/share/doc/php5-common/PEAR
/usr/share/doc/php5-common/CREDITS
/usr/share/doc/php5-common/TODO.gz
/usr/share/doc/php5-common/README.EXT_SKEL.gz
/usr/share/doc/php5-common/README.Zeus.gz
/usr/share/doc/php5-common/README.Debian.gz
/usr/share/doc/php5-common/changelog.Debian.gz
/usr/share/doc/php5-common/README.PHP4-TO-PHP5-THIN-CHANGES.gz
/usr/share/doc/php5-common/changelog.gz
/usr/share/doc/php5-common/TODO.Debian
/usr/share/doc/php5-common/copyright
/usr/share/doc/php5-common/EXTENSIONS.gz
/usr/share/doc/php5-common/CODING_STANDARDS.gz
/usr/share/doc/php5-common/README.SELF-CONTAINED-EXTENSIONS.gz
/usr/share/linda/overrides/php5-common
/usr/share/lintian/overrides/php5-common
/usr/share/php5
/usr/share/php5/php.ini-dist
erik@turbo:/tmp$  


---

### Post by llamakc on 2007-02-16
Did you want to install php5-cli?

---

### Post by erikcw on 2007-02-16
> **llamakc said:**
> Did you want to install php5-cli?

Yes, stupid mistake.  I was able to -f install php5-cli.

I think I have found the root of my problem - apache2 doesn't seem to start.

I run /etc/init.d/apache2 restart and then try to open localhost with firefox.  I get a firefox unable to connect error.  Any idea why apache won't run?

Thanks so much for your help!  I really appreciate it!

---

### Post by llamakc on 2007-02-16
Is all of apache2 installed? 

sudo apt-get install apache2 apache2-common libapache2-mod-php5

---

### Post by erikcw on 2007-02-16
Yes it is. :-(

> 
erik@turbo:/tmp$ sudo apt-get install apache2 apache2-common libapache2-mod-php5
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
apache2 is already the newest version.
apache2-common is already the newest version.
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
erik@turbo:/tmp$     


---

### Post by llamakc on 2007-02-16
Is the server running?

sudo apache2ctl restart

---

### Post by erikcw on 2007-02-16
That got it running!  What does the "ctl" on the command stand for?

Can you recommend a good php IDE?  I'd like something with profiling/debugging support.  Any suggestions?

Thanks!

---

### Post by llamakc on 2007-02-16
ctl probably is short for 'control'. The 'apache2ctl' command allows you to safely stop, restart, and reload the web server. I use that instead of the init scripts inside of /etc/init.d/

I don't know about an IDE. Hopefully somebody comes along. If they don't I would start a new thread or search for that. Congrats on getting it running.

---

