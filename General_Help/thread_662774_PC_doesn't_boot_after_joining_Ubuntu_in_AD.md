---
title: "PC doesn't boot after joining Ubuntu in AD"
date: 2008-01-09
forum: General Help
---

### Post by tanveer on 2008-01-09
Hi,


I have joined a Gusty PC with windows 2003 R2 and using LDAP+Kerberos+pam for authentication againt AD in gusty that is can  login with the windows AD username and password in Gusty without any problem. But when the PC reboots it got stuck showing these messages continuously on screen:

udevd[2780]: nss_ldap: failed to bind to LDAP server ldap://10.10.33.34 : Can't connect LDAP Server
udevd[2780]: Reconnecting to LDAP Server ( Sleeping 1 seconds)......
udevd[2780]: Could not connect to any LDAP Server as cn=scout,cn=Users,dc=abc,dc=com: Cant contact LDAP Server


Whats actually causing this problem ? Any idea?

---

