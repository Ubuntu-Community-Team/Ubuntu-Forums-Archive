---
title: "sssd, auth against multiple domains"
date: 2018-08-19
forum: General Help
---

### Post by iglaj on 2018-08-19
Hi,
I have a child domain in a cloud (data.example.com) and child domain on premises (corp.example.com). Both have in same forest and have two way trust.

In the cloud I have ubuntu16, which I successfully joined to DATA.EXAMPLE.COM.
I can succesfully login to machine using active directory members of DATA domain.

Now I want to be able to login using users from CORP domain.

When I added relevant entries to /etc/krb5.conf for CORP, I was able to kinit against that child domain.

However this doesn't work when I try to ssh to that box using corp users...

This is my /etc/sssd/sssd/conf file:

```

sssd]
domains = data.example.com, corp.example.com
services = nss, pam, ssh, sudo
config_file_version = 2
entry_cache_nowait_percentage = 50


[ssh]


[sudo]


[nss]
filter_users = root,daemon,bin,sys,sync,games,man,lp,mail,news,uucp,proxy,www-data,backup,nobody,syslog,sshd,vagrant,ubuntu,ansible
filter_groups = root,daemon,bin,sys,sync,games,man,lp,mail,news,uucp,proxy,www-data,backup,nobody,syslog,sshd,vagrant,ubuntu,ansible


[pam]
pam_id_timeout = 30


[ldap]


[domain/data.example.com]
ad_domain = data.example.com
ad_hostname = xxx.data.example.com
krb5_realm = DATA.EXAMPLE.COM
realmd_tags = manages-system joined-with-samba
cache_credentials = True
id_provider = ad
krb5_store_password_if_offline = True
default_shell = /bin/bash
ldap_id_mapping = True
use_fully_qualified_names = False
fallback_homedir = /home/%u
access_provider = simple
entry_cache_timeout = 30
simple_allow_groups = ds_dev_os_users
simple_allow_users  =

[domain/corp.example.com]
ad_domain = corp.example.com
ad_hostname = xxx.data.example.com
krb5_realm = CORP.EXAMPLE.COM
realmd_tags = manages-system joined-with-samba
cache_credentials = True
id_provider = ad
krb5_store_password_if_offline = True
default_shell = /bin/bash
ldap_id_mapping = True
use_fully_qualified_names = False
fallback_homedir = /home/%u
access_provider = simple
entry_cache_timeout = 30
simple_allow_groups = ds_dev_os_users
simple_allow_users  =
debug_level = 9


```

---

