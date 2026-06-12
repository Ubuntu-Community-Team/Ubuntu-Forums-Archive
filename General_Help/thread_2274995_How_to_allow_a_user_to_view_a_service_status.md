---
title: "How to allow a user to view a service status?"
date: 2015-04-23
forum: General Help
---

### Post by kevin_vanryck on 2015-04-23
Sorry if this is not the right category to post this.. I wasn't sure..

I added the status command to visudo, but I'm still getting a related error when trying to check the MySQL Status:

```
$ /etc/init.d/mysql status
cat: /var/run/mysqld/mysqld.pid: Permission denied
[info] MySQL is stopped..
```

It always says it's stopped because the permission was denied, but it's actually running.

I added this line in VISUDO:
```
%www-data ALL=NOPASSWD: /etc/init.d/mysql status
```

But the problem is that the user cannot cat the mysqld.pid file. How could I solve this problem? I don't think changing the owner of this file would be a good idea?

Thank you!

---

### Post by kpatz on 2015-04-23
You still need to use sudo:  **sudo /etc/init.d/mysql status** 

The visudo change just allows that user/group to use sudo with that command without having to enter a password.  But you still have to use sudo.

Alternatively, you can get the same status from mysqladmin without using sudo, by running **mysqladmin version**

---

### Post by kevin_vanryck on 2015-04-23
Thanks! That solved it! That was an easy fix haha :D

---

