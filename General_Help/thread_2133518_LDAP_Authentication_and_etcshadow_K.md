---
title: "LDAP Authentication and /etc/shadow *K*"
date: 2013-04-08
forum: General Help
---

### Post by Kissell on 2013-04-08
apt-get -y install libpam-krb5 krb5-user

was installed on a server and /etc/krb5.conf was edited to include LDAP information.

The ! in /etc/shadow for a user was replaced with *K* and that allows LDAP authentication?

I'm just trying to understand how this setup is working, cause it's a little different that I've setup LDAP before.  

What is the *K* ?   user1 can login with local account, and user2 can login using LDAP authentication.

user1:!:15803:0:99999:7:::
user2:*K*:15803:0:99999:7:::

---

