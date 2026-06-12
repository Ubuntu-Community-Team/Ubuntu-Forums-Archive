---
title: "slapd unmet dependencies on ubuntu 12.04"
date: 2013-07-18
forum: General Help
---

### Post by powershell on 2013-07-18
Hi,

Was trying to install mongodb on my ubuntu 12.04, however i run into slapd unmet dependencies which i have zero idea how to resolve.

```

christian@ubuntu:~$ sudo apt-get install mongodb-10gen
[sudo] password for christian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 slapd : Depends: libldap-2.4-2 (= 2.4.28-1.1ubuntu4.2) but 2.4.28-1.1ubuntu4.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
christian@ubuntu:~$ 

```

When i run the command apt-get -f install i ran into these errors:

```

christian@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  slapd
The following packages will be upgraded:
  slapd
1 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,727 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of slapd:
 slapd depends on libldap-2.4-2 (= 2.4.28-1.1ubuntu4.2); however:
  Version of libldap-2.4-2 on system is 2.4.28-1.1ubuntu4.3.
dpkg: error processing slapd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Hope somebody out there can help me out on this. As this ubuntu machine is also running my oracle 10g database and i dont want to set up from scratch again :(

---

### Post by slickymaster on 2013-07-18
Hi powershell, welcome to the forums.

Do you have **ldap-utils** and **libldap** on your system? You can confirm it running:```
dpkg -l | egrep "libldap|ldap-utils"
```

Also, see [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/994533](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/994533)

---

### Post by powershell on 2013-07-18
Hi slickymaster,

Thanks for the speedy response. Yes i confirm that i do have ldaputils and libldap

```

christian@ubuntu:~$ dpkg -l | egrep "libldap|ldap-utils"
ii  ldap-utils                             2.4.28-1.1ubuntu4.3                        OpenLDAP utilities
ii  libldap-2.4-2                          2.4.28-1.1ubuntu4.3                        OpenLDAP libraries
rc  libldap-2.4-2:i386                     2.4.28-1.1ubuntu4.2                        OpenLDAP libraries

```

I also have earlier removing libldap-2.4-2 which resulted to:

```

christian@ubuntu:~$ sudo apt-get remove libldap-2.4-2
[sudo] password for christian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cups : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 evolution-data-server : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 evolution-exchange : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 gconf-service-backend : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 ldap-utils : Depends: libldap-2.4-2 (= 2.4.28-1.1ubuntu4.3) but it is not going to be installed
 libcurl3 : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 libcurl3-gnutls : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 libcurl3-nss : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 libevolution : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 libsmbclient : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 samba-common-bin : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 seahorse : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 slapd : Depends: libldap-2.4-2 (= 2.4.28-1.1ubuntu4.2) but it is not going to be installed
 smbclient : Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




```

---

### Post by slickymaster on 2013-07-18
Can you try running ```
sudo apt-get install --reinstall libldap-2.4-2
``` to see if that fixes the issue?

---

### Post by powershell on 2013-07-19
Thanks for tirelessly responding to my inquiries. 

I have managed to solve the problem by running the following commands:

```

sudo apt-get remove --purge slapd
sudo apt-get install -y slapd


```

---

