---
title: "SSSD ldap auth not binding correctly"
date: 2012-12-12
forum: General Help
---

### Post by TerrySoucy on 2012-12-12
I am having troubles with getting SSSD to auth against my ldap server with a bind_dn.  I turned off anonymous bind on the ldap server, and had no issues with getting SSSD in Ubuntu 12.04 to work with the ldap_default_bind_dn, but for some reason, Ubuntu 10 with the same credentials will NOT work. It looks like SSSD attempts to make an anonymous bind, even though a correct (and recognized) ldap_default_bind_dn  ...

sssd log ..

[sssd[be[internal.blah.com]]] [dp_get_options] (6): Option ldap_default_bind_dn has value cn=Directory Reader,dc=internal,dc=blah,dc=com
[sssd[be[internal.blah.com]]] [dp_get_options] (6): Option ldap_default_authtok_type has value password
[sssd[be[internal.blah.com]]] [dp_get_options] (6): Option ldap_default_authtok has a binary value.
...
...
[sssd[be[internal.blah.com]]] [sdap_get_generic_done] (6): Search result: Inappropriate authentication(48), Anonymous access is not allowed.

ldap log ..

[12/Dec/2012:15:32:37 -0400] conn=139 fd=67 slot=67 connection from 10.72.100.196 to 10.72.100.151
[12/Dec/2012:15:32:37 -0400] conn=139 op=0 UNPROCESSED OPERATION - Anonymous access not allowed
[12/Dec/2012:15:32:37 -0400] conn=139 op=0 RESULT err=48 tag=101 nentries=0 etime=0
[12/Dec/2012:15:32:37 -0400] conn=139 op=1 UNBIND

sssd.conf information ..

[domain/internal.blah.com]
debug_level = 10
enumerate = true
cache_credentials = true

id_provider = ldap
#access_provider = ldap
auth_provider = krb5
chpass_provider = krb5

ldap_uri = ldaps://ldap.internal.blah.com
ldap_krb5_init_creds = false
ldap_schema = rfc2307bis
ldap_default_bind_dn = cn=Directory Reader,dc=internal,dc=blah,dc=com
ldap_default_authtok_type = password
ldap_default_authtok = passW0rd
ldap_search_base = cn=accounts,dc=internal,dc=blah,dc=com
ldap_tls_reqcert = demand
ldap_tls_cacert = /etc/ssl/certs/ca.pem

krb5_kdcip = kerberos.internal.blah.com
krb5_realm = INTERNAL.BLAH.COM
krb5_changepw_principle = kadmin/changepw
krb5_auth_timeout = 15
krb5_kpasswd = kerberos.internal.blah.com

I can perform an ldapsearch from the same host using simple auth to ldaps with no errors, and I have verified that the SSL cert is trusted by the client using openssl s_client.  I've attempted to get this working without SSL and I end up with the same results.

---

### Post by sgallagh on 2012-12-13
> **TerrySoucy said:**
> I am having troubles with getting SSSD to auth against my ldap server with a bind_dn.  I turned off anonymous bind on the ldap server, and had no issues with getting SSSD in Ubuntu 12.04 to work with the ldap_default_bind_dn, but for some reason, Ubuntu 10 with the same credentials will NOT work. It looks like SSSD attempts to make an anonymous bind, even though a correct (and recognized) ldap_default_bind_dn  ...


Older versions of SSSD do not behave properly when anonymous auth is turned off completely on the LDAP server. This is technically a violation of the LDAP standard (which requires that the RootDSE be accessible anonymously no matter what). The reason for this is that before initiating the authenticated connection, we first connect to the RootDSE anonymously to ask it what are the capabilities of the system (which includes the available authentication methods for that server as well as available plugins).

Newer versions of SSSD (1.8.3 and later) now have a workaround for this problem. If it is denied access anonymously it will then just make a best guess and try to connect with an authenticated connection.

So your choices here are

[LIST=1]
[*]Update to SSSD 1.8.3 or later
[*]Reconfigure the LDAP server so that it allows anonymous binds on the RootDSE. You can continue to disallow anonymous binds to the rest of the tree.
[/LIST]

---

### Post by TerrySoucy on 2012-12-13
Allowing anon bind to RootDSE was the key.  Problem solved. Many thanks!

---

