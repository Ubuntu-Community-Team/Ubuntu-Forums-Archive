---
title: "Access denied to mysql console and phpMyAdmin"
date: 2017-04-01
forum: General Help
---

### Post by vbmark on 2017-04-01
In phpMyAdmin I get:

```

#1045 - Access denied for user 'root'@'localhost' (using password: YES)
mysqli_real_connect(): (HY000/1045): Access denied for user 'root'@'localhost' (using password: YES)
```

In Konsole:

```

sudo mysql --user=root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
```

Tried:

```

sudo mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

I've uninstalled and reinstalled mysql.  I've tried some --no-grant-tables stuff.  I'm out of ideas.

Thank you.

EDIT: Fixed with purge, install, granted permissions on folders.

---

