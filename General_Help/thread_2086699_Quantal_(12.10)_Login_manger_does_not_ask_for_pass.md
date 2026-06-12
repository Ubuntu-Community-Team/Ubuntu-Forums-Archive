---
title: "Quantal (12.10) Login manger does not ask for password when using SSSD"
date: 2012-11-21
forum: General Help
---

### Post by skinnyquiver on 2012-11-21
[LIST]
[*]Ubuntu 12.10 gui does not prompt for password for network users

[*]I have been using SSSD to allow authentication to our AD server. 

[*]My configuration works on all prior versions of ubuntu at least back to 10.04. 

[*]This only happens when using gui from command line I am able to login as the user and it prompts for a password.

[*]Under user accounts for the network user the option for Automatic Login is set to off

[*]Command line login works correctly this is only a problem from the gui login page
[/LIST]


To recreate this issue:

1.) install 12.10
2.) install packages ntp sssd libnss-sss libpam-sss krb5-user
3.) configure sssd example below
4.) verify that sfu has been setup on AD server and user has been configured with a uid
5.) put your AD cert in the directory supplied
SSSD EXAMPLE
[SIZE="1"]
[sssd]
config_file_version = 2
reconnection_retries = 3
sbus_timeout = 30
services = nss, pam
domains = example.com

[nss]
filter_groups = root
filter_users = root
reconnection_retries = 3

[pam]
reconnection_retries = 3
debug_level = 3

[domain/EXAMPLE.COM]
enumerate = true
min_id = 1
id_provider = ldap
ldap_uri = ldaps://DC1.example.com/
ldap_user_search_base = dc=example,dc=com
ldap_group_search_base = dc=example,dc=com
ldap_default_bind_dn = CN=binduser,CN=users,dc=example,dc=com
ldap_default_authtok_type = password
ldap_default_authtok = bindpassword

ldap_user_object_class = user
ldap_user_name = sAMAccountName
ldap_user_uid_number = uidNumber
ldap_user_gid_number = gidNumber
ldap_user_home_directory = unixHomeDirectory
ldap_user_shell = loginShell
ldap_user_principal = userPrincipalName
ldap_user_member = msSFU30PosixMemberOf

ldap_group_object_class = group
ldap_group_name = sAMAccountName
ldap_group_gid_number = gidNumber
ldap_group_member = member
ldap_tls_cacertdir = /etc/ssl/certs/
ldap_tls_cacert = /etc/ssl/certs/adcert.pem

[domain/example.com]
ldap_id_use_start_tls = False
cache_credentials = True
id_provider = ldap
auth_provider = krb5
chpass_provider = krb5
debug_level = 3
ldap_schema = rfc2307bis
ldap_force_upper_case_realm = true
krb5_realm = example.com
ldap_search_base = DC=example,DC=com
ldap_uri = ldaps://DC1.example.com/
krb5_kpasswd = DC1.example.com
krb5_kdcip = DC1.example.com
ldap_tls_cacertdir = /etc/ssl/certs/
ldap_tls_cacert = /etc/ssl/certs/adcert.pem
[/SIZE]

---

### Post by lykwydchykyn on 2012-11-21
You should probably report this at lauchpad.  UF is not a bug tracker.

---

### Post by skinnyquiver on 2012-11-21
I am not sure if this is a bug or if something in the configuration has changed to cause this issue but ok I will post this in launchpad

---

### Post by skinnyquiver on 2012-11-26
[Launchpad Bug #1081797]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1081797")

---

