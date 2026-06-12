---
title: "Ubuntu Server - bittorrent installation"
date: 2007-02-07
forum: General Help
---

### Post by Uricta-Wave on 2007-02-07
Im using Ubuntu server..

This is a bit of a newbie question, but where is the WWW folder to put my web pages (recently downloaded apache)

---

### Post by etank on 2007-02-07
If you installed apache2 from the repos then it is in ```
/var/www
```

---

### Post by llamakc on 2007-02-07
This is defined in your /etc/apache2/sites-enabled/default (which is a symlink to /etc/apache2/sites-available/default.

By default,this default is /var/www which is where you would put files so that they show up when you browse to [http://your.site/](http://your.site/)

PS: What does "bittorrent" have to do with the configuration of Apache2? And also, when you say you downloaded apache, you do mean that you installed it from the repositories with apt-get/aptitude, correct?

---

### Post by Uricta-Wave on 2007-02-07
ok.. i figured it out...

/var/www

cheers guys.

---

