---
title: "How can I make changing from MySQL to MariaDB go smoother?"
date: 2015-12-21
forum: General Help
---

### Post by Gottier on 2015-12-21
I've got a few computers that I use for website development, and they're all running the common LAMP stack. Recently my host where I have some production websites changed from MySQL to MariaDB, so I thought I'd update the development machines, and I've got a couple done, but feel like I'm stumbling through, and wondering if it can be done easier, smoother, better, etc.

Here's what I did in the terminal:

```
sudo apt-get remove --purge mysql-server mysql-client mysql-common
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get install software-properties-common
sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xcbcb082a1bb943db
sudo add-apt-repository 'deb [arch=amd64,i386] http://sfo1.mirrors.digitalocean.com/mariadb/repo/10.1/ubuntu trusty main'
sudo apt-get update
sudo apt-get install mariadb-server
sudo service apache2 restart
apt-get install mariadb-client libmariadbclient-dev libmariadbd-dev phpmyadmin
sudo apt-get install mariadb-client libmariadbclient-dev libmariadbd-dev phpmyadmin
sudo service apache2 restart
cd /usr/share/phpmyadmin
ll
sudo cp ./config.sample.inc.php ./config.inc.php
sudo nano ./config.inc.php
sudo service apache2 restart
cd /etc/phpmyadmin
ll
sudo nano config.inc.php 
sudo service apache2 restart
ll
cat config-db.php 
sudo nano config-db.conf
sudo nano config-db.php
locate config.inc.php
sudo nano /var/lib/phpmyadmin/config.inc.php
sudo nano config.inc.php 
sudo dpkg-reconfigure -plow phpmyadmin
sudo service apache2 restart
sudo nano config.inc.php 
sudo service mysql restart
sudo service apache2 restart
sudo apt-get install php5-mysql
sudo apt-get install php5-mysqlnd
sudo service mysql restart
sudo service apache2 restart
```

The main issue, and why it took so long was that I couldn't access phpmyadmin. It appears that when I install mariadb I need to tell the installer to create the database, and I think I've been telling it to keep the existing one. Also, towards the end I had to install mysqlnd because I was getting a mismatch error from PHP. 

So, now that you can see what's troubling me, can you help make this easier? I've got some more computers to update, and I'd like to do it in a better way where I have confidence that I did everything right.

---

