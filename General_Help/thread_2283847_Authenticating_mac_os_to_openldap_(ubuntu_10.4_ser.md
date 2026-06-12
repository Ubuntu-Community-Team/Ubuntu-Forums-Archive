---
title: "Authenticating mac os to openldap (ubuntu 10.4 server)"
date: 2015-06-25
forum: General Help
---

### Post by Acep_Saepudin on 2015-06-25
Hi All,
I have installed openldap from [this]("https://hermanbanken.nl/2011/01/22/openldap-server-mac-osx-clients/") tutorial, when i create new user for login from my mac ,i catch the error like this :
```
Jun 25 14:25:27 proxy slapd[1650]: conn=1033 op=1 do_extended: unsupported operation "1.3.6.1.4.1.1466.20037"Jun 25 14:25:32 proxy slapd[1650]: <= bdb_equality_candidates: (ou) not indexed
Jun 25 14:26:47 proxy slapd[1650]: last message repeated 2 times
Jun 25 14:26:58 proxy slapd[1650]: <= bdb_equality_candidates: (ou) not indexed
Jun 25 14:28:25 proxy slapd[1650]: SASL [conn=1099] Failure: no secret in database
Jun 25 14:28:28 proxy slapd[1650]: SASL [conn=1101] Failure: no secret in database
Jun 25 14:28:29 proxy slapd[1650]: SASL [conn=1103] Failure: no secret in database
Jun 25 14:49:02 proxy slapd[1650]: SASL [conn=1135] Failure: no secret in database
Jun 25 14:52:32 proxy slapd[1650]: SASL [conn=1138] Failure: no secret in database
Jun 25 14:52:39 proxy slapd[1650]: SASL [conn=1141] Failure: no secret in database


```


Please help me and sorry for my english

---

### Post by Bucky Ball on 2015-06-25
Welcome. Can't help with this, but I can inform you that 10.04, server and desktop, are no longer supported. Advise you upgrade to a supported release. 14.04 LTS best for a server. Good luck.

---

