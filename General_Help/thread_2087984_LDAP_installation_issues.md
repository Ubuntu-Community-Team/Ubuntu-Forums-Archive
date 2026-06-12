---
title: "LDAP installation issues"
date: 2012-11-25
forum: General Help
---

### Post by apoth on 2012-11-25
I'm really struggling to get an LDAP installation working to the point that I can import my ldif file.

Any ideas on where the below ends? Thanks in advance.

```
$ sudo aptitude remove --purge ldap-utils slapd -y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

$ sudo aptitude install slapd ldap-utils -y
The following NEW packages will be installed:
  ldap-utils libodbc1{a} libperl5.14{a} libslp1{a} slapd 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,290 kB of archives. After unpacking 5,711 kB will be used.
Preconfiguring packages ...              
Selecting previously unselected package libodbc1.
(Reading database ... 49882 files and directories currently installed.)
Unpacking libodbc1 (from .../libodbc1_2.2.14p2-5ubuntu3_amd64.deb) ...
Selecting previously unselected package libperl5.14.
Unpacking libperl5.14 (from .../libperl5.14_5.14.2-6ubuntu2.1_amd64.deb) ...
Selecting previously unselected package libslp1.
Unpacking libslp1 (from .../libslp1_1.2.1-7.8ubuntu1_amd64.deb) ...
Selecting previously unselected package slapd.
Unpacking slapd (from .../slapd_2.4.28-1.1ubuntu4.2_amd64.deb) ...
Selecting previously unselected package ldap-utils.
Unpacking ldap-utils (from .../ldap-utils_2.4.28-1.1ubuntu4.2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Setting up libodbc1 (2.2.14p2-5ubuntu3) ...
Setting up libperl5.14 (5.14.2-6ubuntu2.1) ...
Setting up libslp1 (1.2.1-7.8ubuntu1) ...
Setting up slapd (2.4.28-1.1ubuntu4.2) ...
  Backing up /etc/ldap/slapd.d in /var/backups/slapd-2.4.28-1.1ubuntu4.2... done.
 * Starting OpenLDAP slapd                                                                                                                                                                                        [ OK ] 
Setting up ldap-utils (2.4.28-1.1ubuntu4.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

$ sudo dpkg-reconfigure slapd
 * Stopping OpenLDAP slapd                                                                                                                                                                                        [ OK ] 

  Creating initial configuration... 
Loading the initial configuration from the ldif file () failed with
the following error while running slapadd:
    ldif_read_record: include file:///etc/ldap/schema/core.ldif failed

$ sudo ls /etc/ldap/schema/|wc -l
0
```

It's a 12.04 instance btw.

---

