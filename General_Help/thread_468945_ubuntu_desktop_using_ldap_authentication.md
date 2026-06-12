---
title: "ubuntu desktop using ldap authentication"
date: 2007-06-09
forum: General Help
---

### Post by whitmad on 2007-06-09
I have installed a ubunu feisty on a trial desktop and am having difficulty configuring to use ldap authentication against a fedora server. Other clients (fedora) authenticate successfully, but the ubuntu desktop machine fails. I can connect to the ldap server from ubuntu using "ldapsearch -h 192.168.0.101 -x .....".

libnss-ldap and libpam.ldap are both installed and have correct connection details for the ldap server, but any attempt to login using a ldap account fails with:

pam_ldap: ldap_simple_bind Can't contact LDAP server

in auth.log

I've tried both with a binddn and bindpw in libnss-ldap.conf and pam-ldap.conf, and without.

The host connection I have configured in these files is:

host ldap://192.168.0.101/

which I would have though wpuld try to connect in the same manner as the ldapsearch command above (without a binddn). Anyone any ideas?

One more oddity. When logging in (using a local user id), I have to enter my password twice.

---

### Post by whitmad on 2007-06-10
both problems fixed - used uri instead of host, and "use_first_pass"

---

