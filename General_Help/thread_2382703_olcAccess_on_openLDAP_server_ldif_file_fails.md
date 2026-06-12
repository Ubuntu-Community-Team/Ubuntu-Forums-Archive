---
title: "olcAccess on openLDAP server ldif file fails"
date: 2018-01-16
forum: General Help
---

### Post by sahulkko on 2018-01-16
I need some ACLs on my ldap server but have hard time writing proper ldif file for it.

My ldif file is following:
[TABLE="width: 500"]
[TR]
[TD] dn: olcDatabase={1}mdb,cn=config
 changetype: modify
 add: olcAccess
 olcAccess: {0} to attrs=userPassword,shadowLastChange by
 self write by anonymous auth by * none
 add: olcAccess
 olcAccess: {1} to dn.subtree="ou=People,dc=ilmarinen,dc=himanet,dc=net" by
 dn="cn=ldapadmin,ou=People,dc=ilmarinen,dc=himanet,dc=net" write
 add: olcAccess
 olcAccess: {2} to dn.subtree="ou=Groups,dc=ilmarinen,dc=himanet,dc=net" by
 dn="cn=ldapadmin,ou=People,dc=ilmarinen,dc=himanet,dc=net" write[/TD]
[/TR]
[/TABLE]

when i try:
[TABLE="width: 500"]
[TR]
[TD]ldapmodify -n -v -f config.ldif[/TD]
[/TR]
[/TABLE]

It works and doesn't give  any error. with following output:
[TABLE="width: 500"]
[TR]
[TD]!modifying entry "olcDatabase={1}mdb,cn=configchangetype: modifyadd: olcAccessolcAccess: {0} to attrs=userPassword,shadowLastChange by self write by anonymous auth by * noneadd: olcAccessolcAccess: {1} to dn.subtree="ou=People,dc=ilmarinen,dc=himanet,dc=net" bydn="cn=ldapadmin,ou=People,dc=ilmarinen,dc=himanet,dc=net" write add: olcAccessolcAccess: {2} to dn.subtree="ou=Groups,dc=ilmarinen,dc=himanet,dc=net" bydn="cn=ldapadmin,ou=People,dc=ilmarinen,dc=himanet,dc=net" write"[/TD]
[/TR]
[/TABLE]

byt when I try to implement it with:
[TABLE="width: 500"]
[TR]
[TD]sudo ldapmodify -a -x -W -D "cn=admin,dc=ilmarinen,dc=himanet,dc=net" -f config.ldif[/TD]
[/TR]
[/TABLE]

I get following error:
[TABLE="width: 500"]
[TR]
[TD]adding new entry "olcDatabase={1}mdb,cn=configchangetype: modifyadd: olcAccessolcAccess: {0} to attrs=userPassword,shadowLastChange by self write by anonymous auth by * noneadd: olcAccessolcAccess: {1} to dn.subtree="ou=People,dc=ilmarinen,dc=himanet,dc=net" bydn="cn=ldapadmin,ou=People,dc=ilmarinen,dc=himanet,dc=net" write add: olcAccessolcAccess: {2} to dn.subtree="ou=Groups,dc=ilmarinen,dc=himanet,dc=net" bydn="cn=ldapadmin,ou=People,dc=ilmarinen,dc=himanet,dc=net" write"
ldap_add: Invalid DN syntax (34)
    additional info: invalid DN[/TD]
[/TR]
[/TABLE]

I have searched for an answer but so far nothing has helped. Hope someone can shed light on this matter.

---

### Post by abhishek-papanna on 2018-05-28
You do not need multiple "add: olcAccess", if you do that you might need to seperate each with a '-'. 
Try this
dn: olcDatabase={1}mdb,cn=config
changetype: modify
add: olcAccess
olcAccess: to attrs=userPassword,shadowLastChange 
 by self write 
 by anonymous auth 
 by * none
olcAccess: to dn.subtree="ou=People,dc=ilmarinen,dc=himanet,dc=n et" 
 by dn="cn=ldapadmin,ou=People,dc=ilmarinen,dc=himanet ,dc=net" write
olcAccess: to dn.subtree="ou=Groups,dc=ilmarinen,dc=himanet,dc=n et" 
 by dn="cn=ldapadmin,ou=People,dc=ilmarinen,dc=himanet ,dc=net" write

Remove the numbers within {} unless you need it. ldapmodify will take care of it.

Also try  ldapmodify -H ldapi:// -Y EXTERNAL -f config.ldif instead. Should work considering you do not have any custom user for mdb database.

---

