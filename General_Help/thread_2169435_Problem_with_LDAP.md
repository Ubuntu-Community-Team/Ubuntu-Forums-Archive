---
title: "Problem with LDAP"
date: 2013-08-22
forum: General Help
---

### Post by Felas on 2013-08-22
Hi,
i have this problem, i install OpenLdap in a virtualserver with virtualbox. I try to import in Eclipse with LDAP Browser a LDIF file, but i have this error when i try to auth.:

LDAP: error code 53 - no global superior knowledge

how i can modify the slapd config ?

---

### Post by jjaison-daniel on 2013-08-22
try on suffix cn=config

---

### Post by jjaison-daniel on 2013-08-22
or cn=schema

---

