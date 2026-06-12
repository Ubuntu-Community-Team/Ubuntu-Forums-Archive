---
title: "Apache, PHP, MySQL on a Desktop system"
date: 2006-08-11
forum: General Help
---

### Post by okok on 2006-08-11
I would like to install Apache, PHP and MySQL for development puposes on a desktop system that is used mainly for other purposes.

In windows I used to start Apache and Mysql by simply running an executable or starting a service.

Can I have the same in Ubuntu: Have these installed but not running, and start and stop them at will just when I need to work with them? If so, how do I do that? Please take into account in your answer that I am quite new to Linux (as you can probably tell from my question).

---

### Post by kaffelars on 2006-08-11
A simple way of installing these things is the XAMPP package (not as in deb-package, but still easy :))

You can download it [here]("http://www.apachefriends.org/en/xampp-linux.html"), you also find good instructions there :)

---

### Post by tomtom_in_eire on 2006-08-11
Hi,

Good news: this is possible ! :D 
you will have to install apache/php/mysql first. To do that, you can run a command such as ```
sudo apt-get install <package_to _install>
```.
Then, if you want to start the services, you can just go to:
**System > Administration > Services**
Select the service you want to stop/start (e.g. Apache web server), check or uncheck the box, click OK - You're done!

Good luck.

---

### Post by okok on 2006-08-11
Thank you both. The XAMPP seems very convenient.

---

### Post by Subbu.exe on 2006-08-11
Well, I Prefer doing it the Wiki Way..

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by az on 2006-08-11
Yes.  It's much simpler to just install
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server
and use the native LAMP stack.  You have much more control and you can easily put your work into a production environment afterwards.

---

### Post by okok on 2006-08-11
Thank you all for your replies.

---

