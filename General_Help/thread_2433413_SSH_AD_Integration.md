---
title: "SSH AD Integration"
date: 2019-12-18
forum: General Help
---

### Post by justinba-ibm on 2019-12-18
I've recently been trying to roll out AD integration to our DNS servers, but am hitting a roadblock. I have this working without issue on my 16.04 test server, and I've already deployed it to my production RHEL servers, but am having issues deploying it to the production 16.04 servers. 

The only place that I'm seeing any errors is in the auth logs:

Dec 18 16:16:27 pbmns sshd[9013]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=X.X.X.X  user=justinba
Dec 18 16:16:27 pbmns sshd[9013]: pam_sss(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=X.X.X.X user=justinba
Dec 18 16:16:27 pbmns sshd[9013]: pam_sss(sshd:auth): received for user justinba: 10 (User not known to the underlying authentication module)
Dec 18 16:16:29 pbmns sshd[9013]: Failed password for justinba from X.X.X.X port 44572 ssh2

This is using the same credentials as were used with realm to join to the domain. Here are some pertinent config files:

root@pbmns:/etc# cat krb5.conf
[libdefaults]
default_realm = FUSION.[REDACTED].COM
rdns = false
dns_lookup_kdc = true
dns_lookup_realm = true

[realms]
FUSION.[REDACTED].COM = {
kdc = fusion.[redacted].com
admin_server = fusion.[redacted].com
}


root@pbmns:/etc# cat sssd/sssd.conf 
[sssd]
domains = fusion.[redacted].com
config_file_version = 2
services = nss, pam

[domain/fusion.[redacted].com]
ad_domain = fusion.[redacted].com
krb5_realm = FUSION.[REDACTED].COM
realmd_tags = manages-system joined-with-adcli 
cache_credentials = True
id_provider = ad
krb5_store_password_if_offline = True
default_shell = /bin/bash
ldap_id_mapping = True
use_fully_qualified_names = True
fallback_homedir = /home/%d/%u
access_provider = ad


root@pbmns:/etc# cat realmd.conf 
[users]
 default-home = /home/%D/%U
 default-shell = /bin/bash

[active-directory]
 default-client = sssd
 os-name = Ubuntu-Server
 os-version = 16.04

[service]
 automatic-install = no

[FUSION.[REDACTED].COM]
 fully-qualified-names = yes
 automatic-id-mapping = no
 user-principal = yes
 manage-system = yes


I'm joined to the domain without issue:

root@pbmns:/etc# realm list
fusion.[redacted].com
  type: kerberos
  realm-name: FUSION.[REDACTED].COM
  domain-name: fusion.[redacted].com
  configured: kerberos-member
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin
  login-formats: %U@fusion.[redacted].com
  login-policy: allow-realm-logins

And it looks like SSH is utilizing pam_sss, but for one reason or another it's returning a user not known error. All systems are NTP so there's no time drift. Any assistance in troubleshooting this would be greatly appreciated. Thanks.

/jgb

---

