---
title: "CUPS not working and cant run &quot;sudo dpkg --configure -a&quot;"
date: 2014-11-03
forum: General Help
---

### Post by Dan_Lee on 2014-11-03
When trying to troubleshoot CUPS not working, I try to run sudo dpkg --configure -a
and then get this.... Im no Ubuntu expert and need some help, my printing isnt working and want to get to the bottom of it. 


```
Setting up apache2 (2.4.10-1ubuntu1) ...
insserv: warning: script 'K36cups' missing LSB tags and overrides
insserv: warning: script 'cups' missing LSB tags and overrides
insserv: There is a loop at service grub-common if started
insserv: There is a loop between service smbd and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service hwclock at depth 3
insserv: There is a loop between service cups and udev if started
insserv:  loop involving service udev at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service smbd and cups if started
insserv:  loop involving service cups at depth 5
insserv:  loop involving service smbd at depth 4
insserv:  loop involving service vboxweb-service at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service smbd and cups if started
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 6
insserv:  loop involving service mountdevsubfs at depth 3
insserv:  loop involving service mountkernfs at depth 1
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: Starting cups depends on grub-common and therefore on system facility `$all' which can not be true!
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package apache2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ocsinventory-reports:
 ocsinventory-reports depends on apache2; however:
  Package apache2 is not configured yet.


dpkg: error processing package ocsinventory-reports (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2 (>= 2.4); however:
  Package apache2 is not configured yet.


dpkg: error processing package libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.5.12+dfsg-2ubuntu4.1~) | libapache2-mod-php5filter (>= 5.5.12+dfsg-2ubuntu4.1~) | php5-cgi (>= 5.5.12+dfsg-2ubuntu4.1~) | php5-fpm (>= 5.5.12+dfsg-2ubuntu4.1~); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not installed.
  Package php5-fpm is not installed.


dpkg: error processing package php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ocsinventory-server:
 ocsinventory-server depends on apache2; however:
  Package apache2 is not configured yet.


dpkg: error processing package ocsinventory-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache2
 ocsinventory-reports
 libapache2-mod-php5
 php5
 ocsinventory-server

```


I also get errors when trying to refresh cups with a similar error

---

### Post by tgalati4 on 2014-11-03
What version of Ubuntu?  CUPS comes installed by default.  So, was CUPS working before and now it is not working?  Or, was CUPS not working ever, and now you are trying to troubleshoot?

```
cat /etc/issue
lsb_release -a
uname -a
```

The command you used tries to reconfigure all packages that have not been configured.  You can just try to reconfigure CUPS only.  But first check your log files in /var/log/cups.

---

### Post by Dan_Lee on 2014-11-03
> **tgalati4 said:**
> What version of Ubuntu?  CUPS comes installed by default.  So, was CUPS working before and now it is not working?  Or, was CUPS not working ever, and now you are trying to troubleshoot?

```
cat /etc/issue
lsb_release -a
uname -a
```

The command you used tries to reconfigure all packages that have not been configured.  You can just try to reconfigure CUPS only.  But first check your log files in /var/log/cups.


No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


I have tried CUPS only - can you tell me how I can view those lose files, I reasonably new to Linux (although come from a IBM command line background)

Yes was working on 14.04 no problem, but 14.10 its blown up completely

---

### Post by Dan_Lee on 2014-11-03
Looks in the [COLOR=#000000]/var/log/cups.[/COLOR] and nothing in there since the 1st November - error log is empty

---

### Post by Dan_Lee on 2014-11-03
Ive tried to remove and re-install CUPS and get this

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cups-core-drivers printer-driver-gutenprint
Suggested packages:
  cups-bsd printer-driver-hpcups hplip cups-pdf gutenprint-doc
The following NEW packages will be installed
  cups cups-core-drivers printer-driver-gutenprint
0 to upgrade, 3 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/560 kB of archives.
After this operation, 1,844 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
Selecting previously unselected package cups-core-drivers.
(Reading database ... 241480 files and directories currently installed.)
Preparing to unpack .../cups-core-drivers_1.7.5-3ubuntu2_amd64.deb ...
Unpacking cups-core-drivers (1.7.5-3ubuntu2) ...
Selecting previously unselected package cups.
Preparing to unpack .../cups_1.7.5-3ubuntu2_amd64.deb ...
Unpacking cups (1.7.5-3ubuntu2) ...
Selecting previously unselected package printer-driver-gutenprint.
Preparing to unpack .../printer-driver-gutenprint_5.2.10-3_amd64.deb ...
Unpacking printer-driver-gutenprint (5.2.10-3) ...
Processing triggers for man-db (2.7.0.2-2) ...
Setting up apache2 (2.4.10-1ubuntu1) ...
ERROR: Module mpm_prefork is enabled - cannot proceed due to conflicts. It needs to be disabled first!
dpkg: error processing package apache2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up cups-core-drivers (1.7.5-3ubuntu2) ...
Setting up cups (1.7.5-3ubuntu2) ...
Setting up printer-driver-gutenprint (5.2.10-3) ...
Errors were encountered while processing:
 apache2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by tgalati4 on 2014-11-03
CUPS uses a web server to administer your printers ([http://localhost:631](http://localhost:631)).  It looks like *apache2* is broken.  Of course, you can set up printers using the "Printers" dialog in the Control Center.  I'm running 14.04, so I can't help with a 14.10 issue.  If you are new to linux, you might consider sticking with 14.04.  The mid-cycle version (14.10) is only supported for a few months.

---

### Post by raccoonstrait on 2014-11-04
Hi Dan_Lee,

I had this issue yesterday. I tried using Synaptic to re-install most things cups related, and since my printer is HP, most things HP related. It did not work. I kept getting errors when trying to connect to the Cups server. 

What did work for me was removing the printer in the system Printers dialog, and then setting up the printer all over. I am currently on Ubuntu 14.10, which is where the issue started, I had no problems with it on 14.04.

I would also like to mention that dpkg-reconfigure -a does not appear to be there anymore, and I do miss it. It has resolved many issues for me in the past (created some as well, as I lost the desktop after running it not too long ago).

raccoonstrait

---

