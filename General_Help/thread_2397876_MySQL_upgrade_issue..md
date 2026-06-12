---
title: "MySQL upgrade issue."
date: 2018-08-04
forum: General Help
---

### Post by starwars-geek98 on 2018-08-04
Hello everyone,

I recently ran the software updater in Ubuntu and then I ran sudo apt upgrade in terminal to make sure everything is updated. So, I came accross this problem: MySQL couldn't upgrade. I tried the dpkg option from the recovery mode but no luck. The message displayed gives insight but I need a little guidance. Furthermore I couldn't find my error code.

**ERROR:** ```
Error occurred: The mysql.session exists but is not correctly configured. The mysql.session needs SELECT privileges in the performance_schema database and the mysql.db table and also SUPER privileges.mysql_upgrade failed with exit status 5
dpkg: error processing package mysql-server-5.7 (--configure):
 installed mysql-server-5.7 package post-installation script subprocess returned error exit status 1

```

Does anybody know anything about this?

Thanks in advance!

*P.S I am using Ubuntu 18.04.*

---

