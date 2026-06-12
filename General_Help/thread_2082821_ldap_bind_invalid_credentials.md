---
title: "ldap_bind invalid credentials"
date: 2012-11-10
forum: General Help
---

### Post by psycho5 on 2012-11-10
Hi,

Refering to the link:

[https://help.ubuntu.com/12.04/serverguide/openldap-server.html]("https://help.ubuntu.com/12.04/serverguide/openldap-server.html")

I am trying to follow the steps and everything going fine except when adding a new .ldif file using the instructions:

```

ldapadd -x -D cn=admin,dc=example,dc=com -W -f add_content.ldif

Enter LDAP Password: ********
adding new entry "ou=People,dc=example,dc=com"

adding new entry "ou=Groups,dc=example,dc=com"

adding new entry "cn=miners,ou=Groups,dc=example,dc=com"

adding new entry "uid=john,ou=People,dc=example,dc=com"

```

I get this error for ldap:

ldap_bind: Invalid credentials (49) 

even though I know my ldap admin password, this is on a virtual machine and I am just doing this to educate myself so please tell me why am i getting this error?

I didn't forget my admin password, I remember all the passwords, this is a simple vbox simulation.

Please advise.

---

