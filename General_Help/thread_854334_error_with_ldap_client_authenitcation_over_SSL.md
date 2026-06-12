---
title: "error with ldap client authenitcation over SSL"
date: 2008-07-09
forum: General Help
---

### Post by georgemoore13 on 2008-07-09
(Using Ubuntu 8.04 Server)

I'm currently trying to authenticate with an ldap server. it works fine on the standard port (389)

Using 
```
ldapsearch -x -H ldap://ldap.school.edu:389 "uid=example"
```

it works fine, but when I try to authenticate over SSL using

```
ldapsearch -Z -x -H lpads://ldap.school.edu:636 "uid=example"
```

I get this error:
"ldap_sasl_interactive_bind_s: Can't contact LDAP server (-1)"


I know the port is open and working because openssl s_client works fine.

Any help is appreciated.

Edit: Here is part of my ldap.conf, the rest is default.

```

uri ldaps://ldap.school.edu:636
base dc=tufts,dc=edu

```

---

