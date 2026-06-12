---
title: "Drupal-5.1"
date: 2007-10-23
forum: General Help
---

### Post by jthigpen on 2007-10-23
Hello, can someone help me troubleshoot my drupal installation.

Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

It's actually installed and running, but I can't get apt-get to quit complaining.  I don't know what to do.

apt-get seems miffed:

root@www:/usr/share/otrs/bin# apt-get install drupal-5.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
drupal-5.1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up drupal-5.1 (5.1-0ubuntu2.1) ...
dbconfig-common: writing config to /etc/dbconfig-common/drupal-5.1.conf
Replacing config file /etc/drupal/5.1/sites/default/dbconfig.php with new version
dpkg: error processing drupal-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 drupal-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

I'm sure you need more info, but I'm not sure what else, please advise.

Thanks,

-jt

---

### Post by rsambuca on 2007-10-23
Have you tried uninstalling and then re-installing?

Also, why are you running as root?

---

### Post by thk on 2007-10-23
The packaging appears to be highly broken. File a bug report.

---

### Post by thk on 2007-10-23
> **rsambuca said:**
> Also, why are you running as root?

Lots of people do and it is really OK. Stick to the topic of the request.

---

### Post by rsambuca on 2007-10-23
> **thk said:**
> Lots of people do and it is really OK. Stick to the topic of the request.

It is a legitimate question for a first time poster.

---

