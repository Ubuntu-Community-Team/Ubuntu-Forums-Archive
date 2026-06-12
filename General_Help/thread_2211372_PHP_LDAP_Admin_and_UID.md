---
title: "PHP LDAP Admin and UID"
date: 2014-03-15
forum: General Help
---

### Post by sim085 on 2014-03-15
Hello, I have installed OpenLDAP and PHP LDAP Admin. I created a new user and I noticed this user was given a uid of 1000. I ready on the Ubuntu documentation that this should ideally be 5000 or some other high number in order to avoid conflicts with real accounts. I can go on the user and change the uid to 5000, however next time I create a new user I am given the uid of 1000 automatically. Is there a way how to force phpldapadmin to give uid's that are more then 5000?

---

