---
title: "how you can open phpmyadmin by typing site_name/phpmyadmin"
date: 2008-06-14
forum: General Help
---

### Post by volmark on 2008-06-14
I don&#8217;t really understand how you can open phpmyadmin by typing site_name/phpmyadmin ([http://sitename/myadmin](http://sitename/myadmin)). I&#8217;ve inspected web root path (/var/www/)  and could not see any directories or redirections named &#8220;phpmyadmin&#8221;
Any suggestions??

---

### Post by NikoC on 2008-06-14
Hmmz I just did a search in terminal as follows:
locate phpmyadmin |grep config

And this file for example is referring to the 'localhost' folder:
/usr/share/phpmyadmin/config.inc.php

Cheers.

---

