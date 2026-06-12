---
title: "Ubuntu Server MySQL reset password"
date: 2007-12-23
forum: General Help
---

### Post by bohsocks on 2007-12-23
Hey.... I am currently installing a LAMP server and need help resolving an issue I'm about to encounter.... 

I set up all my normal configurations and when it came to picking a root password for MySQL I reached for the keyboard and dropped it.... in the process I hit a few keys and enter.... which is what my new MySQL password is going to be.... 

Since I have no clue what keys I hit... I won't be able to use MySQL without resetting the password.... how do I do this?

---

### Post by chippy99 on 2007-12-23
Stop mysql by typing

/etc/init.d/mysql stop

from a console type

 ```
sudo mysqld_safe --skip-grant-tables --user=root &
```

you can then login to mysql as root without a password and reset it.

---

