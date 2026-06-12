---
title: "ldap pam authentication"
date: 2018-11-03
forum: General Help
---

### Post by etannor on 2018-11-03
I need some help authenticating users to an ldap server 16.04. I have installed libnss-ldapd and other ldap components. 
I am able to getent the user and su to the user which means I am able to bind to the ldap server.
However ldap users get authentication failure when trying to login via ssh. 

```

In /var/log/auth.log 
sshd[9169]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=1xx.xxx.xxx  user=xxxx
sshd[9169]: Failed password for xxx from 1xx.xxx.xxx port 53561 ssh2

```

I will appreciate  a working config for /etc/pam.d/common-* or /etc/pam.d/sshd that I can compare against? I suspect that one of these  configurations is causing me grief.

---

