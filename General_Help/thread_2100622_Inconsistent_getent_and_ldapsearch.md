---
title: "Inconsistent getent and ldapsearch"
date: 2013-01-02
forum: General Help
---

### Post by MrtnLowr on 2013-01-02
Hi All,

I've seen several threads on this topic but none quite seem to match the situation here.  I have a working OpenLDAP server and several clients which work happily together for login authentication.  Now I'm trying to add a new client to the pool but can't get getent to return the users so they don't appear on the login screen.

The following work fine : 
```
ldapsearch -x -h wagner uid=martin
```
and
```
ldapsearch -D "cn=admin,dc=cmri,dc=hey,dc=nhs,dc=uk" -W -h wagner uid=martin
```
but
```
getent passwd martin
```
returns nothing.

I have nslcd installed and that reports the following after the getent command:
> nslcd: [8b4567] DEBUG: connection from pid=3155 uid=0 gid=0
nslcd: [8b4567] DEBUG: nslcd_passwd_byname(martin)
nslcd: [8b4567] DEBUG: myldap_search(base="dc=cmri,dc=hey,dc=nhs,dc=uk", filter="(&(objectClass=posixAccount)(uid=martin))")
nslcd: [8b4567] DEBUG: ldap_initialize(ldap://wagner.cmri.hey.nhs.uk/)
nslcd: [8b4567] DEBUG: ldap_set_rebind_proc()
nslcd: [8b4567] DEBUG: ldap_set_option(LDAP_OPT_PROTOCOL_VERSION,3)
nslcd: [8b4567] DEBUG: ldap_set_option(LDAP_OPT_DEREF,0)
nslcd: [8b4567] DEBUG: ldap_set_option(LDAP_OPT_TIMELIMIT,0)
nslcd: [8b4567] DEBUG: ldap_set_option(LDAP_OPT_TIMEOUT,0)
nslcd: [8b4567] DEBUG: ldap_set_option(LDAP_OPT_NETWORK_TIMEOUT,0)
nslcd: [8b4567] DEBUG: ldap_set_option(LDAP_OPT_REFERRALS,LDAP_OPT_ON)
nslcd: [8b4567] DEBUG: ldap_set_option(LDAP_OPT_RESTART,LDAP_OPT_ON)
nslcd: [8b4567] DEBUG: ldap_simple_bind_s("cn=admin,dc=cmri,dc=hey,dc=nhs,dc=uk","*****") (uri="ldap://wagner.cmri.hey.nhs.uk/")
nslcd: [8b4567] failed to bind to LDAP server ldap://wagner.cmri.hey.nhs.uk/: Can't contact LDAP server: Success
nslcd: [8b4567] no available LDAP server found, sleeping 1 seconds
nslcd: [8b4567] no available LDAP server found


More or less the same happens if binddn & bindpw are absent from nslcd.conf.

Can anybody suggest a fix for this?

All help gratefully appreciated.

Cheers!

---

### Post by luvshines on 2013-01-02
Maybe I am asking a dumb question but is the ldap server reachable by the FQDN ?

---

### Post by MrtnLowr on 2013-01-03
@luvshines

Thanks, sometimes the answer is staring you in the face.  Updated hosts file and of course it worked.

Cheers!

---

