---
title: "ldapmodify problem"
date: 2013-11-28
forum: General Help
---

### Post by alexclifford47 on 2013-11-28
I'm trying to add my ldap user on an OpenLDAP 2.4 server to have full permissions like the default admin user. I have tried the following but nothing appears to change. Could someone please point me in the right direction to get this working?

```
[COLOR=#000000]root@ldap:/etc/ldap/slapd.d# ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=config '(olcDatabase={1}hdb)' olcAccess[/COLOR]dn: olcDatabase={1}hdb,cn=config
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymou
 s auth by dn="cn=admin,dc=example,dc=com" write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by self write by dn="cn=admin,dc=example,dc=com" writ
 e by * read

root@ldap:/etc/ldap/slapd.d# cat /root/add_write_access.ldif 
dn: olcDatabase={1}hdb,cn=config
changetype: modify
add: olcAccess
olcAccess: to * by self write by dn="cn=admin,dc=example,dc=com" write by dn="uid=alex,ou=Users,dc=example,dc=com" write by * read

root@ldap:/etc/ldap/slapd.d# ldapmodify -a -n -v -D "cn=admin,dc=example,dc=com" -y /etc/ldapscripts/ldapscripts.passwd -H "ldap://localhhost" -f ~/add_write_access.ldif 
add olcAccess:
    to * by self write by dn="cn=admin,dc=example,dc=com" write by dn="uid=alex,ou=Users,dc=example,dc=com" write by * read
!modifying entry "olcDatabase={1}hdb,cn=config"

root@ldap:/etc/ldap/slapd.d# ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=config '(olcDatabase={1}hdb)' olcAccess
dn: olcDatabase={1}hdb,cn=config
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymou
 s auth by dn="cn=admin,dc=example,dc=com" write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by self write by dn="cn=admin,dc=example,dc=com" writ [COLOR=#000000] e by * read[/COLOR]
```

---

### Post by alexclifford47 on 2013-12-01
For what it's worth for others, I had a few things wrong and will list here what "fixed" this for me.

1. In my examples above I was still including the -n switch for ldapmodify which will only show what it is doing without committing any changes. oops.

2. My final .ldif file was:
```
root@ldap:~# cat add_write_access.ldif
dn: olcDatabase={1}hdb,cn=config
changetype: modify
replace: olcAccess
olcAccess: {0}to attrs=userPassword,shadowLastChange by self write by anonymous auth by dn="cn=admin,dc=example,dc=com" write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by self write by dn="cn=admin,dc=example,dc=com" write by dn="uid=alex,ou=Users,dc=example,dc=com" write by * read
```

3. I manually to get this change to work by running:
```
root@ldap:~# ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f ~/add_write_access.ldif 
modifying entry "olcDatabase={1}hdb,cn=config"
```

I had been attempting the following previously:
```
root@ldap:~# ldapmodify -a -v -D "cn=admin,dc=example,dc=com" -y /etc/ldapscripts/ldapscripts.passwd -H "ldap://localhost" -f ~/add_write_access.ldif
ldap_initialize( ldap://localhost:389/??base )
add olcAccess:
    {2}to * by self write by dn="cn=admin,dc=example,dc=com" write by dn="uid=alex,ou=Users,dc=example,dc=com" write by * read
modifying entry "olcDatabase={1}hdb,cn=config"
ldap_modify: Insufficient access (50)
```

4. The resulting ldapsearch after the above changes was then showing correctly (and testing confirmed):
```
root@ldap:~# ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=config '(olcDatabase={1}hdb)' olcAccess
```

---

