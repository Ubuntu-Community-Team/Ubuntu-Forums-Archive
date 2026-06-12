---
title: "Login to Ubuntu takes too long using AD  user"
date: 2021-07-11
forum: General Help
---

### Post by fpramilo on 2021-07-11
Hi Everyone,

Can some help me out. I'm having problem which it takes too long to Login to Ubuntu using AD Simple user
Pls. my configuration below. 

root@ubuntutest1:/etc/sssd# cat sssd.conf


[sssd]
domains = test.com
config_file_version = 2
services = nss, pam


[pam]
pam_pwd_expiration_warning = 14
pam_account_expired_message = Account expired
pam_account_locked_message = Account locked


[domain/test.com]
ad_enable_gc = False
ad_domain = test.com
krb5_realm = TEST.COM
realmd_tags = manages-system joined-with-samba
cache_credentials = True
id_provider = ad
krb5_store_password_if_offline = True
default_shell = /bin/bash
ldap_id_mapping = True
homedir_substring = /home/TEST
fallback_homedir = %H/%u
access_provider = simple
simple_allow_groups = GRP_LinuxAdmin, 
simple_allow_users = 12100023, 121000024,

---

