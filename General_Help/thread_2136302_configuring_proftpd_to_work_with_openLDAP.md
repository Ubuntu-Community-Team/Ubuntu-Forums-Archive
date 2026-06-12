---
title: "configuring proftpd to work with openLDAP"
date: 2013-04-17
forum: General Help
---

### Post by datamind on 2013-04-17
[FONT=Droid Serif]Hello.[/FONT]

[FONT=Droid Serif]I'm trying to make proftpd authenticate against openLDAP. openLDAP is working, I've got Owncloud setup to authenticate against it. I've now spent quite a few hours trying to get proftpd to do the same. Trying all sorts of different guides. I can log in to Proftpd with my local admin account, but not with any users stored in LDAP.[/FONT]

[FONT=Droid Serif]here is my /etc/proftpd/ldap.conf[/FONT]

```
[FONT=Droid Serif]<IfModule mod_ldap.c>[/FONT]

[FONT=Droid Serif]    LDAPServer ldap://localhost/??sub[/FONT]
[FONT=Droid Serif]    LDAPBindDN "cn=admin,dc=offset,dc=com[/FONT][FONT=Droid Serif]" "adminpassword"[/FONT]
[FONT=Droid Serif]    LDAPUsers ou=People,dc=offset,dc=com[/FONT][FONT=Droid Serif] (uid=%u) (uidNumber=%u)[/FONT]
[FONT=Droid Serif]    LDAPGroups ou=Groups,dc=offset,dc=com[/FONT]

[FONT=Droid Serif]    </IfModule>[/FONT]
```

[FONT=Droid Serif]P.S. mod_ldap.c is loaded in the other configs.[/FONT]

[FONT=Droid Serif]I hope some one can help me.[/FONT]
[FONT=Droid Serif]Thanks[/FONT]

---

