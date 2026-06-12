---
title: "MySQL users issue - can't log in to phpmyadmin as root"
date: 2018-04-27
forum: General Help
---

### Post by spectatorx on 2018-04-27
This one is complicated and the weirdest problem i've ever had with linux in general. Straight to the point: i've installed lamp on 18.04 the usual way i do this, the method with which lamp used to be working for me on 16.04, 16.10, 17.04, 17.10 but now for the first time i'm getting serious problems and i have no idea why. LAMP is set up and configured, when i try to log in to phpmyadmin as root i'm getting error message:
mysqli_real_connect(): (HY000/1698): Access denied for user 'root'@'localhost'

I can log in as user named "phpmyadmin" but then i'm unable to do anything. Also as root i can't log in via mysql workbench.

MySQL version: 5.7.21PHPMyAdmin version: 4.8.0.1

Usually i was just logging into phpmyadmin as root and everything was working fine. Since today as i've installed ubuntu 18.04 and lamp i'm unable to.

Here is instruction i'm using to install lamp:

> 

sudo apt-add-repository ppa:ondrej/php -y && sudo apt-add-repository ppa:ondrej/apache2 -y && sudo apt-add-repository ppa:nijel/phpmyadmin -y

sudo apt-get install -f apache2 mysql-server mysql-client php7.2-mysql php7.2-dev php7.2-curl php7.2-json php7.2-cgi php7.2 phpmyadmin libapache2-mod-php7.2 php7.2-mbstring php7.2-fpm php7.2-cli php7.2-common php7.2-gd php7.2-bz2 php7.2-xml php7.2-intl php-pear php-imagick php7.2-imap php-memcache php7.2-pspell php7.2-recode php7.2-sqlite3 php7.2-tidy php7.2-xmlrpc php7.2-xsl php-gettext php-apcu php7.2-zip php7.2-phpdbg php7.2-ldap php7.2-pgsql php7.2-snmp php7.2-pdo php7.2-xdebug

To set up phpmyadmin under Apache all you need to do is to include at end of file /etc/apache2/apache2.conf the following line:
Include /etc/phpmyadmin/apache.conf

sudo service apache2 restart



---

