---
title: "[SOLVED] phpmyadmin doesn't put a folder into /var/www"
date: 2008-06-18
forum: General Help
---

### Post by alingham on 2008-06-18
Hi people!

I've recently tried to install phpmyadmin on my Ubuntu 8.04 box.
It installs fine, except that it doesn't come up with the configuration screens that the tutorials say should come up, and  that going to [http://localhost/](http://localhost/) doesn't show the "phpmyadmin" folder...
Going to /var/www/ shows that there is no sign of a phpmyadmin folder anywhere...
Yes - mysql-server is installed...

Any suggestions?

---

### Post by Nepherte on 2008-06-18
I'm not sure why it doesn't make an entry in /var/www. Maybe you should just remove the phpmyadmin package and install it from source: [https://help.ubuntu.com/community/phpMyAdmin#head-e247a300fd82da72778e0b34d828cb571d7af17a](https://help.ubuntu.com/community/phpMyAdmin#head-e247a300fd82da72778e0b34d828cb571d7af17a) You'll have phpmyadmin running in no time.

---

### Post by justleen on 2008-06-18
```
locate phpmyadmin
```

phpmy admin doenst run fron /var/www if you installed the packages, but from /usr/share
the config is located in /etc/

this is quite common for installed packages..

---

