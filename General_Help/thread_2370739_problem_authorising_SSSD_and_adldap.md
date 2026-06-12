---
title: "problem authorising SSSD and ad/ldap"
date: 2017-09-06
forum: General Help
---

### Post by Linuxisgod! on 2017-09-06
hi guys 
i have installed and configured SSSD and i have loged the server to the domain and can perform Ldap searches without issue, the problem is that if i try and do a getent passwd (username) or getent passwd (username.fqdn) it returns nothing.
if i try and su - user it complains that "there is no passwd for that user" and i am at a loss as all looks good.
is there something i have missed or is there something on the AD/Ldap server that i need to promote to allow remote linux authentication.
all the configs on the server look correct any help much appreciated.
regards
andrew

---

