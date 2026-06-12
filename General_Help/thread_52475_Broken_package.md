---
title: "Broken package"
date: 2005-07-27
forum: General Help
---

### Post by bdika on 2005-07-27
I have webmin-apache package installed on my system and I can't uninstall it or reinstall it without getting the following error message:

Removing webmin-apache ...
/etc/webmin/webmin.acl: No such file or directory
dpkg: error processing webmin-apache (--remove):
 subprocess pre-removal script returned error exit status 2
/etc/webmin/webmin.acl: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 webmin-apache
E: Sub-process /usr/bin/dpkg returned an error code (1)

When I install webmin it tells me the latest version is already installed but I can't get webmin to start. I get the following when trying to install webmin:

dad@ubuntu:~$ sudo apt-get install webmin
Reading package lists... Done
Building dependency tree... Done
webmin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up webmin-apache (1.210a-2~5.04ubp1) ...
/etc/webmin/webmin.acl: No such file or directory
dpkg: error processing webmin-apache (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 webmin-apache
E: Sub-process /usr/bin/dpkg returned an error code (1)
dad@ubuntu:~$

Any help would be greatly appreciated.

Regards,
Bill Dika

---

### Post by bdika on 2005-07-28
I got this to uninstall by creating the missing file:

/etc/webmin/webmin.acl

however, the webmin I get after installing using apt-get has no tabs for "services, hardware, etc" only one for configuring webmin itself.

Regards,
Bill Dika

---

