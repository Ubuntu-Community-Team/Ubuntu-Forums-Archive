---
title: "ubuntu updater stopped working"
date: 2016-05-05
forum: General Help
---

### Post by ELMIT on 2016-05-05
I tried to install an MTA today. I used Ubuntu Software Center to install postfix.

Several hours it did not finish it. I canceled and tried in a terminal:

sudo apt-get install postfix

The screen showed:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libntdb1 python-ntdb
Use 'apt-get autoremove' to remove them.
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin dovecot-common postfix-cdb
The following packages will be REMOVED:
  lsb-invalid-mta
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 1 to remove and 3 not upgraded.
Need to get 0 B/1,097 kB of archives.
After this operation, 3,502 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: lsb-invalid-mta: dependency problems, but removing anyway as you requested:
 lsb-core depends on lsb-invalid-mta (>= 4.1+Debian11ubuntu8) | mail-transport-agent; however:
  Package lsb-invalid-mta is to be removed.
  Package mail-transport-agent is not installed.
  Package lsb-invalid-mta which provides mail-transport-agent is to be removed.
 lsb-core depends on lsb-invalid-mta (>= 4.1+Debian11ubuntu8) | mail-transport-agent; however:
  Package lsb-invalid-mta is to be removed.
  Package mail-transport-agent is not installed.
  Package lsb-invalid-mta which provides mail-transport-agent is to be removed.

(Reading database ... 236939 files and directories currently installed.)
Removing lsb-invalid-mta (4.1+Debian11ubuntu8) ...
Selecting previously unselected package postfix.
(Reading database ... 236934 files and directories currently installed.)
Preparing to unpack .../postfix_2.11.3-1ubuntu2_amd64.deb ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing archive /var/cache/apt/archives/postfix_2.11.3-1ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_2.11.3-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Now nothing works in regards of update manager.

How to fix?

---

### Post by courtney2 on 2016-05-05
Have you tried doing a "sudo apt-get clean"? I think that should fix your updater issues, but not installing postfix since I see there are missing dependencies

---

### Post by ELMIT on 2016-05-05
> **courtney2 said:**
> Have you tried doing a "sudo apt-get clean"? I think that should fix your updater issues, but not installing postfix since I see there are missing dependencies

Yes, but the Software Updater window just shows Checking for updates... after that again.

---

