---
title: "Error pam_ldap"
date: 2006-11-06
forum: General Help
---

### Post by gekkos on 2006-11-06
Hi,
I am using Ubuntu 6.06 LTS with LDAP Authentication. Everything was working till after I installed the updates. Now I cannot authenticate anymore with LDAP.
The error that I got is:
[COLOR="Red"]pam_ldap: could not open secret file /etc/pam_ldap.secret (No such file or directory)[/COLOR]

but when I test with
```
getent passwd
```
I get the list of LDAP users.
Anyone an idea was went wrong with the update.
Thanks

---

### Post by gekkos on 2006-11-06
Found the problem.
Updating libpam-ldap changed the config file pam_ldap.conf
After changes pam_ldap.conf back to original everythings works fine again.

---

