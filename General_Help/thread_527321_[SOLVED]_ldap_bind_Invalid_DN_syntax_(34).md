---
title: "[SOLVED] ldap_bind: Invalid DN syntax (34)"
date: 2007-08-16
forum: General Help
---

### Post by cancaseiro on 2007-08-16
Hi!

Trying to set up OpenLDAP but when I tried to ```
ldapadd -x -D "cn=admin,dc=<test>,dc=<ekool>,dc=<ee>" -W -f init.ldif
``` I got ```
error ldap_bind: Invalid DN syntax (34)
        additional info: invalid DN
```

Can someone help me?

---

### Post by cancaseiro on 2007-08-16
I removed <>  :oops: Anyways now I have error ```
ldap_bind: Invalid credentials (49)
```

---

