---
title: "LDAP: ldapadd as root exits with no write access to parent"
date: 2013-08-30
forum: General Help
---

### Post by ptsneves on 2013-08-30
In the LDAP server guide it is sugested that the root user always has full privileges but when i run a command like 

```
sudo ldapadd -Y EXTERNAL -H ldapi:/// -D cn=admin,dc=example,dc=com
```

and i get 
```
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
adding new entry "cn=project_group,ou=Groups,dc=example,dc=com"
ldap_add: Insufficient access (50)
        additional info: no write access to parent
```

What can i do to be able to login this way?

---

