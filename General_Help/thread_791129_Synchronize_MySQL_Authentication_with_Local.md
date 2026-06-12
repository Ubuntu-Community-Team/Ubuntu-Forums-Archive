---
title: "Synchronize MySQL Authentication with Local?"
date: 2008-05-11
forum: General Help
---

### Post by illiaster on 2008-05-11
Greetings!

Is it possible to synchronize the MySQL authentication with the local account? I'm currently providing free shell access to our developers (all .NET programmers) -- as a way so they can learn PHP, Linux, and other opensource technologies.

I use phpmyadmin for them to access the MySQL database and toy around with it.

Question is, is it possible for phpmyadmin/MySQL to authenticate or synchronize its password with the local linux account? So whenever they change their local password, they don't have to do it twice through phpmyadmin.

Or if not, can I use pam-mysql/nss-mysql so that local authentication occurs through the same user table as MySQL -- I've done this for logins, but cannot get passwd program to sync the password.

Any help would be appreciated, thanks!

---

