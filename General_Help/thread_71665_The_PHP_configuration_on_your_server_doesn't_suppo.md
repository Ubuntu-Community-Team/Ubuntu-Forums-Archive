---
title: "The PHP configuration on your server doesn't support the database type that you chose"
date: 2005-10-04
forum: General Help
---

### Post by waynejkruse10 on 2005-10-04
Hello, im using Ubuntu Hoary and i installed Apache (2.0.53-5ubuntu5.3), PHP (4:4.3.10-10ubuntu4 and Mysql-server (4.0.23-3ubuntu2.1) and i get this error:

> The PHP configuration on your server doesn't support the database type that you chose

When i try to install PHPBB

Thanks
Wayne

---

### Post by simon w on 2005-10-04
See what phpinfo() says...
```
echo "<? phpinfo(); ?>" > phpinfo.php 
```
Move phpinfo.php in your document root directory and point your web browser at it ([http://localhost/phpinfo.php](http://localhost/phpinfo.php)) and search for mysql.  If it's not there, php isn't configured for MySQL support.

I'm not familar with Ubuntu's LAMP packages so I can't help anymore I'm affriad.

---

### Post by waynejkruse10 on 2005-10-04
Ok, ill do that now, by the way, i have also installed the package PHP4-MYSQL.

---

### Post by waynejkruse10 on 2005-10-04
> 
Warning: Unknown(/var/www/phpinfo.php): failed to open stream: Permission denied in Unknown on line 0

Warning: (null)(): Failed opening '/var/www/phpinfo.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Thats what it spits out

---

### Post by simon w on 2005-10-05
Try
```

sudo chmod 664 /var/www/phpinfo.php

```
and try [http://localhost/phpinfo.php](http://localhost/phpinfo.php) again.

---

