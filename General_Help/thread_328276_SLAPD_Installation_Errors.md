---
title: "SLAPD Installation Errors"
date: 2006-12-30
forum: General Help
---

### Post by jmoschetti45 on 2006-12-30
When I try to install SLAPD, I get this mess:

```
root@Stephanie:/usr/local/var# apt-get install slapd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  ldap-utils
Recommended packages:
  db4.2-util
The following NEW packages will be installed:
  slapd
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/901kB of archives.
After unpacking 2490kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package slapd.
(Reading database ... 43922 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.2.26-5ubuntu3.1_i386.deb) ...
Setting up slapd (2.2.26-5ubuntu3.1) ...
  Creating initial slapd configuration... done.
  Creating initial LDAP directory... bdb_db_open: Cannot access database directory /usr/local/var/openldap-data (2)
backend_startup_one: bi_db_open failed! (-1)
slap_startup failed
Failed to slapadd this data:
dn: dc=nodomain
objectClass: top
objectClass: dcObject
objectClass: organization
o: nodomain
dc: nodomain

dn: cn=admin,dc=nodomain
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword: {crypt}ze4VnB5kgUdOY
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Ideas?

---

