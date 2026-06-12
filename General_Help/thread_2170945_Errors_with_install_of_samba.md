---
title: "Errors with install of samba"
date: 2013-08-28
forum: General Help
---

### Post by coolecho on 2013-08-28
Hello,

I am running Ubuntu 10.04 Lucid Lynx, and am trying to install samba with "sudo apt-get install samba".
I attempted update of sources list, and then ran aptitude update, and aptitude safe-upgrade before I tried the samba install.

I get the following error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 6,264kB of archives.
After this operation, 17.1MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main samba 2:3.4.7~dfsg-1ubuntu3.10 [6,264kB]
Fetched 6,264kB in 19s (318kB/s)                                                           
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 168159 files and directories currently installed.)
Unpacking samba (from .../samba_2%3a3.4.7~dfsg-1ubuntu3.10_i386.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up samba-common-bin (2:3.4.7~dfsg-1ubuntu3.10) ...
update-alternatives: error: alternative link /usr/bin/nmblookup is already managed by nmblookup.bkup.
dpkg: error processing samba-common-bin (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common-bin; however:
  Package samba-common-bin is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
              Errors were encountered while processing:
 samba-common-bin
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks very much for any help.

---

### Post by GwL3eNC on 2013-08-28
Hello,

what if you try

sudo apt-get -f install 

or

sudo apt-get build-dep samba

---

