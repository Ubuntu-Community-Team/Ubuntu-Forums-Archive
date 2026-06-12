---
title: "GSSAPIDelegateCredentials support in ssh"
date: 2006-10-24
forum: General Help
---

### Post by yangtj207 on 2006-10-24
Does anyone know how to add GSSAPIDelegateCredentials support in ssh? I have installed ssh-krb5 (and other krb5 components). When I add the following line to my /etc/ssh/sshd_config:
GSSAPIDelegateCredentials yes
ssh-krb5 complains:
/etc/ssh/sshd_config: line 103: Bad configuration option: GSSAPIDelegateCredentials
The following options are recognized:

GssapiAuthentication yes
GssapiKeyExchange yes
GssapiUseSessionCredcache yes
GssapiCleanupCreds yes

but I really need GSSAPIDelegateCredentials support. 

Thank you.

---

### Post by TradedManatee on 2008-03-15
There are 2 separate files in /etc/ssh
sshd_config and ssh_config

The GSSAPIDeligateCredentials goes in ssh_config...

Peter

---

