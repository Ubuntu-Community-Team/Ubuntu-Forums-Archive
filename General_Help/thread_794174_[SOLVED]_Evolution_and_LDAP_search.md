---
title: "[SOLVED] Evolution and LDAP search"
date: 2008-05-14
forum: General Help
---

### Post by borobudur on 2008-05-14
In Gutsy and the Evolution version there this worked (still works in a shell):
```
ldapsearch -LLL -x -b 'o=a_user,ou=addressbook,dc=subdomain,dc=dyndns,dc=org' -H ldaps://subdomain.dyndns.org -D 'uid=a_user,ou=users,dc=subdomain,dc=dyndns,dc=org' -W
```If I try this in Hardy it doesn't work. I need to take the user ```
cn=Manager,dc=subdomain,dc=dyndns,dc=org
```Has anyone the same problem?

---

### Post by borobudur on 2008-05-26
Solved! I think I messed up my access control in slapd.conf

PS. How can I set the threat as solved??

---

