---
title: "How to install php for testing purposes only."
date: 2013-02-02
forum: General Help
---

### Post by bluelight0 on 2013-02-02
Hello,

I understand how to use PHP pre-installed on a webserver but it is my first time installing it on my own computer.

I wish to make a setup that allows me to simply have a directory to  place .php files. and then a on and off command so it is not running  when I don't need it.
(so xx.xx.xx.xx/myphpscript.php)

I have tried reading online, but all tutorials point to installing for a full time server.

Ubuntu 12.04

thankyou for reading :smile:

---

### Post by srekcahrai on 2013-02-02
Place your php files inside /var/www directory and goto your fav browser and type
```

localhost/<php filename>

```
in address bar.

---

### Post by bluelight0 on 2013-02-02
> **srekcahrai said:**
> Place your php files inside /var/www directory and goto your fav browser and type
```

localhost/<php filename>

```in address bar.

thankyou, with this I was able to get to the relevant tutorials.

for people searching for this solution:
[http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)
[http://ubuntuforums.org/showthread.php?t=1879868](http://ubuntuforums.org/showthread.php?t=1879868)
[http://www.cyberciti.biz/faq/ubuntu-linux-start-restart-stop-apache-web-server/](http://www.cyberciti.biz/faq/ubuntu-linux-start-restart-stop-apache-web-server/)

---

