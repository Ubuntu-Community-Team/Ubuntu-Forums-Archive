---
title: "LDAP authentication and user priviledges"
date: 2006-08-08
forum: General Help
---

### Post by tiennd on 2006-08-08
Hi,
I have configured Ubuntu Dapper to authenticate successfully with OpenLDAP server.
The problem is: when I use an user account which is from openldap db, not the local account, to login, I can not use audio devices.
I tried to edit user profile: set all priviledges to Default profile (just for testing), but nothing changes.
Another question is: is there any way I can add ldap users to local group?

Thank you,
Regards,

Nguyen Duc Tien
[http://www.dtn.com.vn](http://www.dtn.com.vn)

---

### Post by theinnerlight on 2006-09-16
you can add an ldap user to a local group like this:

adduser <ldap user> <local group>  

So this example would add the LDAP user 'joeuser' to the local group 'webeditors':

adduser joeuser webeditors

---

