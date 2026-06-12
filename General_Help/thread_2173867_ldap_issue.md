---
title: "ldap issue"
date: 2013-09-11
forum: General Help
---

### Post by chakri78 on 2013-09-11
My ldap client system console and ssh sessions hangs/ very very slow response ( even if i logged in with local user name) when ldap server connection is down. Any idea what could be wrong. 

in nsswitch.conf
-----------------------
# pre_auth-client-config # passwd:         compat
passwd: files ldap
# pre_auth-client-config # group:          compat
group: files ldap
# pre_auth-client-config # shadow:         compat
shadow: files ldap


thanks,

---

