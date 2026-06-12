---
title: "Apache2 woes"
date: 2008-01-31
forum: General Help
---

### Post by upthelum on 2008-01-31
Firstly sorry if it's inappropriate posting this here.

Apache2 installed fine but it wont install phpmyadmin for some reason. I've tried restart graceful etc but it wont happen. Webalizer did install though. 

I used this: *apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 php5-mysql libapache2-mod-php5 libapache2-mod-auth-mysql phpmyadmin webalizer*

I can ping the web and the loopback fine and have no connection problems, apt-get update works fine and everything else does too. Can anyone suggest a fix or refer me to somewhere that possibly can please?

Thanks for any suggestions....

---

### Post by PinkFloyd102489 on 2008-01-31
Installing phpMyAdmin from repos didnt work for me. I actually just installed it a few minutes ago. Grab the source from their site, throw it in /var/www/, and change config.sample.inc.php to config.inc.php then you're good to go.

I also changed the dir name from phpMyAdmin-whatever to phpmyadmin, just for ease of use.

---

### Post by upthelum on 2008-01-31
> **PinkFloyd102489 said:**
> Installing phpMyAdmin from repos didnt work for me. I actually just installed it a few minutes ago. Grab the source from their site, throw it in /var/www/, and change config.sample.inc.php to config.inc.php then you're good to go.

I also changed the dir name from phpMyAdmin-whatever to phpmyadmin, just for ease of use.

Thanks again i'll give that a shot tomorrow. 

Great band btw.

---

