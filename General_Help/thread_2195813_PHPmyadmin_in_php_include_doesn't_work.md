---
title: "PHPmyadmin in php include doesn't work"
date: 2013-12-26
forum: General Help
---

### Post by martin.kettle on 2013-12-26
Hi, 

I've installed and configured LAMP server, but although when i type in my computer's IP address/phpmyadmin this brings up the usual phpmyadmin page fine, however if on my index.html page I create some php code which says <?php include 'phpmyadmin';?> this doesn't work. I've checked that .html pages can be parsed by php engine by including some other php include code before this and testing it, so it's just the phpyadmin include which isn't working, any ideas? thanks.

---

### Post by Iowan on 2013-12-26
I'm certainly no expert at PHP, but I'm unfamiliar with "including"  phpmyadmin on a page. I saw [this]("http://askubuntu.com/questions/19127/how-to-access-phpmyadmin-after-installation") on adding "Include /etc/phpmyadmin/apache.conf"  to  /etc/apache2/apache2.conf

---

