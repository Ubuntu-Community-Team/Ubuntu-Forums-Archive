---
title: "How do I set up network authentication?"
date: 2006-11-14
forum: General Help
---

### Post by immesys on 2006-11-14
I need to be able to store usernames and passwords for a bunch of people on one pc on a network and then somehow set it up so that all the other pc's use it for authentication. This way, users could login on any one of the pc's in the lab.

I have no idea what its called, but on most large networks running windows you can set this up (I think it might be called Active Directory), so if windows has it then linux probably had it first.

The only possible solution I could think of was synchronising the shadow and passwd files to each pc every time someone changed their password but I am sure there is a better way.

I've searched for a package in the repositories but I don't really know what to look for.

Thanks

---

### Post by johnnymac on 2006-11-14
Probably what your looking for is OpenLDAP.  

[http://www.openldap.org/](http://www.openldap.org/)

It's a Lightweight Directory Access Protocol (LDAP).  This should get you what you want.

---

