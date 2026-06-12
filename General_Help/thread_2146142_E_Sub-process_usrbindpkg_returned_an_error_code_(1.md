---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-05-17
forum: General Help
---

### Post by Eagleye61 on 2013-05-17
When I try to run the command: "sudo apt-get install deluge" to install Deluge, I get this error.

Here is the full Terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
deluge is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up man-db (2.6.3-3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can someone please HELP?!
THX

---

### Post by matt_symes on 2013-05-17
Hi

Do you have the software centre or update-manager open ? if so then close them.

Kind regards

---

