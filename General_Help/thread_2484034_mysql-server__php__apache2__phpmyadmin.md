---
title: "mysql-server / php / apache2 / phpmyadmin"
date: 2023-02-15
forum: General Help
---

### Post by m-knichel on 2023-02-15
When I first installed mysql-server / php / apache2 / phpmyadmin, something must have gone wrong.  I don't' have a phpmyadmin db in mysql.  I tried to purge everything and reinstall, but now I don't even get prompted for the mysql password.

I removed/purged all 4 packages. and reinstalled again but same problem.

How to I get this sorted out correctly?

M

---

### Post by SeijiSensei on 2023-02-16
I think you need to create a database first.

[https://dev.mysql.com/doc/refman/8.0/en/creating-database.html](https://dev.mysql.com/doc/refman/8.0/en/creating-database.html)

---

### Post by m-knichel on 2023-02-17
The installation of phpmyadmin usually creates the pma database.  However it is not this time...  I just want to remove everything apache2, php, mysql & phpmyadmin so it does so like it should.

---

