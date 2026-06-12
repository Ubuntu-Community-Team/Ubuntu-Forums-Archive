---
title: "sssd joins to domain but saying unknown id when authenticating"
date: 2016-02-09
forum: General Help
---

### Post by william102 on 2016-02-09
I have a ubuntu 12.04 server that I am trying to join to a Windows 2003 AD domain.  I have installed sssd, keberos, samba and all the other necessary packages.  I am able to join the domain using the following command: sudo net ads join -U <username>. When I enter this command it prompts me for the sudo password and then followed by a prompt for my AD password.  After that it says it joined the domain and then I run the test join command and it says the following:

create_local_private_krb5_conf_for_domain: smb_mkstemp failed, for file /var/run/samba/smb_tmp_krb5.3zgh17. Errno Permission denied
create_local_private_krb5_conf_for_domain: smb_mkstemp failed, for file /var/run/samba/smb_tmp_krb5.PESvaR. Errno Permission denied
Join is OK

When I try to look up those files to see if the permissions are correct, they do not exist and I presume this is because they are temp files.  It shows up in AD on the domain controller and I am able to get a keberos ticket so the join seems to be ok.  However, when I go to authenticate, it keeps saying that my ID is unknown.  Why would this be? I have posted my config files below. (I have replaced my actual domain name with example.org)

sssd.conf

```
[sssd]
config_file_version = 2
reconnection_retries = 3
sbus_timeout = 30
services = nss, pam
domains = example.org


[nss]
filter_groups = root
filter_users = root
reconnection_retries = 3


[pam]
reconnection_retries = 3


[domain/example.org]
; Using enumerate = true leads to high load and slow response
enumerate = false
cache_credentials = true


id_provider = ldap
auth_provider = krb5
chpass_provider = krb5


ldap_uri = ldap://dc.example.org
ldap_search_base = DC=example,DC=org
ldap_tls_reqcert = demand
ldap_tls_cacert = /etc/ssl/certs/ca-certificates.crt


krb5_kdcip = dc.example.org
krb5_realm = EXAMPLE.ORG
krb5_changepw_principle = kadmin/changepw
krb5_auth_timeout = 15

```

smb.conf
```

#======================= Global Settings =======================


[global]


## Browsing/Identification ###


# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = EXAMPLE
   client signing = yes
   client use spnego = yes
   kerberos method = secrets and keytab
   realm =EXAMPLE.ORG
   security = ads


# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)


# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no


# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z


# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no



```

---

