---
title: "Get error when do smbldap-populate"
date: 2016-11-05
forum: General Help
---

### Post by sincos2007 on 2016-11-05
Hi All,

I'm working on install smbldap-tools on my Ubuntu 14.04

I have compiled and installed Berkeley DB(4.4.20) and OpenLDAP(2.4.44) successfully. But when I do smbldap-populate, I get error:

adding new entry: ou=Account,dc=du,dc=com
failed to add entry: invalid structural object class chain (organizationalUnit/organization) at /usr/sbin/smbldap-populate line 500.
adding new entry: ou=Users,ou=Account,dc=du,dc=com
failed to add entry: No such object at /usr/sbin/smbldap-populate line 500.
adding new entry: ou=Groups,ou=Account,dc=du,dc=com
failed to add entry: No such object at /usr/sbin/smbldap-populate line 500.
adding new entry: ou=Computers,ou=Account,dc=du,dc=com
failed to add entry: No such object at /usr/sbin/smbldap-populate line 500.
adding new entry: ou=Idmap,ou=Account,dc=du,dc=com
failed to add entry: No such object at /usr/sbin/smbldap-populate line 500.
failed to search entry: invalid DN at /usr/sbin/smbldap-populate line 480.

Thanks for your help

---

