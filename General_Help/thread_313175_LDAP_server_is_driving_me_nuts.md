---
title: "LDAP server is driving me nuts"
date: 2006-12-05
forum: General Help
---

### Post by Little Beast on 2006-12-05
Hi,

For 3 days now I'm trying to set up an LDAP server, but it just won't work.
Whenever I perform an ldapsearch I get this error :
*"ldap_bind: Invalid credentials (49)"*
Searching through this forum didn't help me any further and google tells me my rootpw is incorrect (although I cheched it a million times, and even used clear text).
I would appreciate it a lot if somebody could help me out here.

For what it's worth, here are my slapd.conf and my init.ldif config.


[I]database        bdb
suffix          "dc=example,dc=org"
directory       /home/manager
rootdn          "cn=manager,dc=example,dc=org"
rootpw          {SSHA}tAdvC+tiAXQYdTXez0VfpDJJRqil4+fW
index           objectClass eq,pres
index           ou,cn,mail,sn,givenName eq,pres,sub
index           uidNumber,gidnumber,loginShell eq,pres
index           uid,memberUid eq,pres,sub
index           nisMapName,nisMapEntry eq,pres,sub
lastmod         off
access to attrs=userPassword
        by dn="cn=manager,dc=example,dc=org" write
        by anonymous auth
        by self write
        by * none
access to dn.base="" by * read
access to *
        by dn="cn=manager,dc=example,dc=org" write
        by * read[/I]


[I]dn: dc=example,dc=org
objectClass: dcObject
objectClass: organizationalUnit
dc: example
ou: example

# Test
dn: cn=manager,dc=example,dc=org
cn: manager
objectclass: organizationalRole[/I]

---

