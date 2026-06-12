---
title: "what are htese?"
date: 2007-06-23
forum: General Help
---

### Post by wizekid on 2007-06-23
Errors were encountered while processing:
 postfix
 mailx
 nagios-common
 nagios-mysql
  


i keep getting those erros when i try to do anything! and also  ive searched all over the place and mu ubuntu server edtionb will not find proftd! what else can i use> pure-ftpd will not find either! sry for my bad english!

---

### Post by Maxtorm on 2007-06-23
Not sure about the odd errors, but with respect to ftp, try vsftp.

---

### Post by wizekid on 2007-06-24
```

root@linux:~# aptitude install vsftpd
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up postfix (2.2.10-1ubuntu0.1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: linux.hsd1.fl.comcast.net.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: linux.hsd1.fl.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios-common:
 nagios-common depends on mailx; however:
  Package mailx is not configured yet.
dpkg: error processing nagios-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios-mysql:
 nagios-mysql depends on nagios-common (= 2:1.3-cvs.20050402-8ubuntu7); however:
  Package nagios-common is not configured yet.
dpkg: error processing nagios-mysql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 nagios-common
 nagios-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up postfix (2.2.10-1ubuntu0.1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: misplaced delimiter: linux.hsd1.fl.comcast.net.
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: linux.hsd1.fl.comcast.net.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios-common:
 nagios-common depends on mailx; however:
  Package mailx is not configured yet.
dpkg: error processing nagios-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nagios-mysql:
 nagios-mysql depends on nagios-common (= 2:1.3-cvs.20050402-8ubuntu7); however:
  Package nagios-common is not configured yet.
dpkg: error processing nagios-mysql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 nagios-common
 nagios-mysql
```

this is the error i get after trying to install vsftpd     ive donr alot of readinbg and non leads me anywhere! maybe a linux guru here can help me! this is just a test server im setting up so ill be willing to give you root and ssh into it to check it out! pls do help me! thanks!

---

### Post by wizekid on 2007-06-24
ok so i fixed the errors so thats a done deal!
now how do i set poasswords for rthe ftp login?

---

### Post by Maxtorm on 2007-06-24
From a quick Google, here is a quick and dirty way to set it up: [http://www.netadmintools.com/art355.html](http://www.netadmintools.com/art355.html)

---

