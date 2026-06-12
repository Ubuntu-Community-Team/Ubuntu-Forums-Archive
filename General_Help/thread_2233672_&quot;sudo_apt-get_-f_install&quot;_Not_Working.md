---
title: "&quot;sudo apt-get -f install&quot; Not Working"
date: 2014-07-10
forum: General Help
---

### Post by KYHRL on 2014-07-10
I can't install anything, and whenever I try "sudo apt-get -f install" I recieve the following console output:

**jeffadrake@jeffadrake-K53U:~$ sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libldap-2.4-2
The following NEW packages will be installed:
  libldap-2.4-2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/154 kB of archives.
After this operation, 519 kB of additional disk space will be used.
**Do you want to continue? [Y/n] Y**
(Reading database ... 174637 files and directories currently installed.)
Preparing to unpack .../libldap-2.4-2_2.4.31-1+nmu2ubuntu8_amd64.deb ...
Unpacking libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu8) ...
dpkg: error processing archive /var/cache/apt/archives/libldap-2.4-2_2.4.31-1+nmu2ubuntu8_amd64.deb (--unpack):
 trying to overwrite shared '/etc/ldap/ldap.conf', which is different from other instances of package libldap-2.4-2:amd64
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libldap-2.4-2_2.4.31-1+nmu2ubuntu8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone know how to correct this?  I REALLY don't want to have to uninstall xubuntu and reinstall it.

---

### Post by KYHRL on 2014-07-10
Solved the problem by running terminal command "sudo rm -f /etc/ldap/ldap.conf", then re-running "sudo apt-get -f install".

---

