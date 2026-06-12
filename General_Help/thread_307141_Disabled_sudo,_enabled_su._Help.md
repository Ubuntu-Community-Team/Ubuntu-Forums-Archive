---
title: "Disabled sudo, enabled su. Help"
date: 2006-11-26
forum: General Help
---

### Post by hopspitfire on 2006-11-26
I disabled sudo and enabled su, now I see there is no wheel group so how do I make it so it will prompt me for the root password when I try to access programs that require root?


Or would it be easier to make sudo and gksudo ask for a password separate from my user account? I let my gf use my laptop (I'm not always around so she knows my password) so I don't want her breaking my system.

---

### Post by hopspitfire on 2006-11-26
bump

---

### Post by taurus on 2006-11-26
It is easier to use sudo and to use sudo, you need to belong to groups adm & admin in /etc/group...

```
groups
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

p.s.  Create a new account for her to use but don't put her in groups adm & admin.  Then she can't break your system.  The only thing she would break is her own account and you can recreate it again.

---

### Post by Ramses de Norre on 2006-11-26
You can add the rootpw option in /etc/sudoers (on the "Defaults" line) and set a root password, sudo will then ask that root password instead of the user password.
See man sudoers for more info.

---

