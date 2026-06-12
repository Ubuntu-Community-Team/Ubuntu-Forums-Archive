---
title: "AD user login - issue"
date: 2024-06-01
forum: General Help
---

### Post by eby on 2024-06-01
Ubuntu 22.04 LTS Desktop is integrated with Windows 2019 Active Directory. Users can login to Ubuntu Desktop with their AD credentials. 

However on AD Server event viewer, AD user login is logged as local user(default local login on Ubuntu) with Event ID: 4769, instead of AD user. 

AD group based firewall policies are not working for those who use Ubuntu, as the SSO agent omit all local user logins.

Any help to resolve this issue is appreciated.

Thanks,


----------------------------------------------
[SIZE=4]Windows event Viewer[/SIZE]

```
A Kerberos service ticket was requested.

TargetUserName <local_user>$@<domain.com>
TargetDomainName <domain.com>
ServiceName krbtgt/<domain.com>
ServiceSid S-1-0-0
TicketOptions 0x60000000
TicketEncryptionType 0xffffffff
IpAddress ::ffff:<local ipv4>
IpPort 41842
Status 0xd
LogonGuid {00000000-0000-0000-0000-000000000000}
TransmittedServices -
```



[SIZE=4]Ubuntu Desktop[/SIZE]

```
  
~$ realm list

DOMAIN.COM
  type: kerberos
  realm-name: DOMAIN.COM
  domain-name: DOMAIN.COM
  configured: kerberos-member
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin
  login-formats: %U@DOMAIN.COM
  login-policy: allow-realm-logins
```


```

~$ sudo sssctl domain-status DOMAIN.COM
Online status: Online

Active servers:
AD Global Catalog: dc01.DOMAIN.COM
AD Domain Controller: dc01.DOMAIN.COM

Discovered AD Global Catalog servers:
- dc01.DOMAIN.COM

Discovered AD Domain Controller servers:
- dc01.DOMAIN.COM

```


```

~$ sudo cat /etc/sssd/sssd.conf
[sssd]
domains = DOMAIN.COM
config_file_version = 2
services = nss, pam, ifp

[domain/DOMAIN.COM]
default_shell = /bin/bash
krb5_store_password_if_offline = False
cache_credentials = False
krb5_realm = DOMAIN.COM
realmd_tags = manages-system joined-with-adcli 
id_provider = ad
fallback_homedir = /home/%u@%d
ad_domain = DOMAIN.COM
use_fully_qualified_names = True
ldap_id_mapping = True
access_provider = ad
```

---

