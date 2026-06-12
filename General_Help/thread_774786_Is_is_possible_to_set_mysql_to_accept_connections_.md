---
title: "Is is possible to set mysql to accept connections from a range of ip address?"
date: 2008-04-29
forum: General Help
---

### Post by exactopposite on 2008-04-29
I use mysql for amarok. The music collection (shared via nfs) and mysql database are on one pc on my lan. I know i can set the mysql database to allow login from a particular ip address, but is it possible to set it to work with a range of addresses?

if need be i can go into further detail about what exactly i'm trying to do, but i'm trying to keep the post simple.

---

### Post by ebelog on 2008-04-29
The GRANT command can take wildcards in an IP address.

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'username'@'192.168.1.%'
    ->     IDENTIFIED BY 'some_pass' WITH GRANT OPTION;
```

More info about adding and modifying users in MySQL can be found in the documentation
[http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)

---

### Post by exactopposite on 2008-04-29
> **ebelog said:**
> The GRANT command can take wildcards in an IP address.

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'username'@'192.168.1.%'
    ->     IDENTIFIED BY 'some_pass' WITH GRANT OPTION;
```

More info about adding and modifying users in MySQL can be found in the documentation
[http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)


thanks a lot for this. the problem is that i was trying to use * as a wildcard like 192.168.1.*

---

