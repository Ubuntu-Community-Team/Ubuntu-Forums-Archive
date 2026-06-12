---
title: "After upgrading Lubuntu to 13.10, Apache not enabled sites."
date: 2013-10-21
forum: General Help
---

### Post by QDMLAhW on 2013-10-21
Hello, pals!
After upgrade from lubuntu 13.04 to 13.10, my Apache virtual hosts not work. Seems like it's disabled, but I can't enable it by a2ensite!

Please, anybody, what kind of problem it can be?

(Sorry for my poor English)



[IMG]www.24optom.ru/ubuntu.png[/IMG]

---

### Post by rgoya-a on 2013-11-07
I also had the same problem.

I found out that [you need to rename your "sites available" sites with ".conf" at the end]("http://queirozf.com/reminders/upgrading-apache-to-version-2-4-on-ubuntu-lessons-learned") - then you can enable them and restart apache

---

### Post by rgoya-a on 2013-11-07
Oh and you also need to [reconfigure phpmyadmin]("https://help.ubuntu.com/community/phpMyAdmin"):


[LIST]
[*=left]Since Ubuntu 13.10 (Saucy Salamander), Apache no longer loads configuration files from the /etc/apache2/conf.d directory. Instead, they are loaded from the /etc/apache2/conf-enabled directory. Therefore, if you need to manually include the phpMyAdmin-shipped Apache configuration file, you must run the following:[FONT=inherit][/FONT]
[/LIST]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][/FONT][FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]
[FONT=inherit][/FONT]sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-enabled/phpmyadmin.conf
[FONT=inherit][/FONT]sudo /etc/init.d/apache2 reload

---

