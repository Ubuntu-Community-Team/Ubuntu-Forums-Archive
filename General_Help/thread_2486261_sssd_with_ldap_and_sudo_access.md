---
title: "sssd with ldap and sudo access"
date: 2023-04-24
forum: General Help
---

### Post by solarflow99 on 2023-04-24
On the client side, I have set sssd to use ldap for the backend and its working fine, I also have sudo set to use sssd.  However I have noticed a few things that don't seem right:


[LIST]
[*]There is very little in the Ubuntu docs for this, did I miss something?
[*]Why does /etc/ldap/ldap.conf still have to be there?  I can't even login without it.
[*]Is there a utility to change the authentication mechanism for nsswitch, something like authselect in the RH distros have?
[/LIST]

Thanks,

---

