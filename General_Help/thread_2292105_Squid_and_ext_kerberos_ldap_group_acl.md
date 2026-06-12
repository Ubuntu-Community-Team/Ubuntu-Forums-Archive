---
title: "Squid and ext_kerberos_ldap_group_acl"
date: 2015-08-25
forum: General Help
---

### Post by zakirovr90 on 2015-08-25
Hi guys,
I am having a trouble by trying to configure the squid 3.4.8 in debian 8 to check if a user in a AD group.
My squid is already works with AD by kerberos auth, and AD users can go online, but now I wan to block some sites for groups in AD.
I am trying to check if ext_kerberos_ldap_group_acl works at all by command:
```
/usr/lib/squid3/ext_kerberos_ldap_group_acl -a -d -i -g full_internet@CALLEP.LOCAL
```
but I stumble to this error:
```
kerberos_ldap_group: ERROR: ldap_sasl_interactive_bind_s error: Local error
kerberos_ldap_group: ERROR: Error while binding to ldap server with SASL/GSSAPI: Local error
```
I already installed libsasl2 and gssapi:
```

apt-get install libsasl2-modules-gssapi-mit

```
Here I put all log with error:
[URL="http://pastebin.com/snvi3PSw"]http://pastebin.com/snvi3PSw



[/URL]

Please help! I am so tired by fighting this error.
Or else is there any other method to check users in group and how can I configure that.

---

### Post by ecarlseen2 on 2016-05-30
I'm having the same issue in Xenial - were you able to resolve it? I've found a few things:

1) It correctly identifies potential LDAP servers in our Active Directory environment.
2) The debug messages indicate that it tries to bind to the LDAP server using SASL/GSSAPI even if you specify a username / password.
3) The exact debug messages I'm getting are:
[FONT=courier new]support_ldap.cc(942): pid=17257 :2016/05/29 17:11:51| kerberos_ldap_group: DEBUG: Setting up connection to ldap server <SERVER DNS NAME>:389[/FONT]
[FONT=courier new]support_ldap.cc(953): pid=17257 :2016/05/29 17:11:51| kerberos_ldap_group: DEBUG: Bind to ldap server with SASL/GSSAPI[/FONT]
[FONT=courier new]support_sasl.cc(276): pid=17257 :2016/05/29 17:11:51| kerberos_ldap_group: ERROR: ldap_sasl_interactive_bind_s error: Local error[/FONT]
4) The only packets it's sending to the LDAP server (aside from SYN, FIN, ACK, etc) are "Unbind" requests. So for some reason the LDAP processing is so messed up it's not even really attempting to bind.

---

