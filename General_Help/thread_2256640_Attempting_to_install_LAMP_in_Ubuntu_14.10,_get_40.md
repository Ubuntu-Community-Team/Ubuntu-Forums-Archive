---
title: "Attempting to install LAMP in Ubuntu 14.10, get 404 when attempting to access http://"
date: 2014-12-13
forum: General Help
---

### Post by bobthebot on 2014-12-13
After installing LAMP via tasksel, I'm able to access the "It works" test page at [http://localhost/](http://localhost/) however after creating phptest.php in var/www, I get a 404 when trying to access [http://localhost/phptest.php.](http://localhost/phptest.php.) Any help would be appreciated. 

My www directory:

bartosik@bartosik-ThinkPad-X131e:/var/www$ ls -l
total 12
drwxr-xr-x 2 root root 4096 Dec 13 20:34 html
-rw-r--r-- 1 root root   22 Dec 13 20:45 phptest.php
-rw-r--r-- 1 root root   22 Dec 13 20:36 phptest.php~

The contents of phptest.php:
  
 <?php

phpinfo();

?>

---

### Post by schragge on 2014-12-13
See [thread=2224028]this thread[/thread].

---

