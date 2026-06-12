---
title: "Ubuntu upgraded 16.04 LTS to 18.04 LTS"
date: 2018-11-05
forum: General Help
---

### Post by alexemperor on 2018-11-05
[SIZE=2]**1.** Ubuntu upgraded 16.04 LTS to 18.04 LTS
[FONT=arial]
But when I check phpinfo its showing PHP Version 7.0.22-0[B]ubuntu0.16.04.1

Is there any problem with upgrade ?  how to fix this[/B][/FONT]
**2.** Showing below error in local site installation (mysite.dev)

Fatal error: Uncaught Error: Call to undefined function mb_strtolower() in /home/user/www/mysite/include/functions_insert.php:20 Stack trace: #0 /home/user/www/mysite/index.php(146): insert_tags() #1 {main} thrown in /home/user/www/mysite/include/functions_insert.php on line 20

I tried to install

sudo apt-get install php7.0-mbstring

But getting following error

Package php7.0-mbstring is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'php7.0-mbstring' has no installation candidate


Then tried

sudo apt install php-mbstring

and got 

php-mbstring is already the newest version (1:7.2+60ubuntu1)

Still showing the same error.
[/SIZE]

---

### Post by coffeecat on 2018-11-05
Support not chat.

*Thread moved to **General Help**.*

---

