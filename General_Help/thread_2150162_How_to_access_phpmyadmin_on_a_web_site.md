---
title: "How to access phpmyadmin on a web site?"
date: 2013-05-31
forum: General Help
---

### Post by Mariane on 2013-05-31
Hi, 

I installed apache2, php5, phpmyadmin, mysql-common, mysql-client, mysql-server on a remote server running ubuntu, via apt-get. apache2 is running fine, when I look at the server through a browser I can see the "It works!" message. 

Then I tried to look at [www.mysite.com/phpmyadmin](www.mysite.com/phpmyadmin) and it says "page not found". (I tried to spell it phpMyAdmin but it makes no difference).

I tried to follow the instructions on page:
[http://docs.phpmyadmin.net/en/latest/setup.html#quick-install](http://docs.phpmyadmin.net/en/latest/setup.html#quick-install)
but it is not possible. This page talks about "the phpmyadmin" directory but I have 8 of them! I have no idea which one to go to. 
./var/lib/phpmyadmin
./var/lib/mysql/phpmyadmin
./etc/phpmyadmin
./usr/share/dbconfig-common/data/phpmyadmin
./usr/share/doc-base/phpmyadmin
./usr/share/doc/phpmyadmin
./usr/share/lintian/overrides/phpmyadmin
./usr/share/phpmyadmin

Same with the file config.inc.php which I am supposed to edit. There are 3 them:
./var/lib/phpmyadmin/config.inc.php
./etc/phpmyadmin/config.inc.php
./usr/share/phpmyadmin/setup/frames/config.inc.php

AFAIK, writing something after an IP means pointing to a sub-directory. The "index.html" file created when I installed apache2 is in /var/www
If I look in /var/www, there is no sub-directory called phpmyadmin. There are no sub-directories at all. Should I try a symbolic link or something?

Please, what should I do?

---

### Post by Mariane on 2013-05-31
Got it! 

This page was more helpful:
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

I had to edit the file /etc/apache2/apache2.conf (using nano as root). 
I added the line:
Include /etc/phpmyadmin/apache.conf
at the bottom of this file. 

Then I did 
```

sudo /etc/init.d/apache2 reload
sudo /etc/init.d/apache2 restart

```

Then I could see the phpmyadmin login page, but I could not log in. It said "1045 Cannot log in to the MySQL server". Until I dicovered that the username was "root" and not "admin".

---

