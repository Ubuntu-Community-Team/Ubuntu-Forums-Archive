---
title: "Can't install libcurl4-dev"
date: 2013-03-06
forum: General Help
---

### Post by Mr. ViC on 2013-03-06
Hi guys.

I'm using a tutorial to install PHP 5.3 and FastCGI.

```
Install/Compile PHP 5.3 (and FastCGI)

sudo apt-get install libapache2-mod-fastcgi -y
sudo a2enmod actions fastcgi rewrite include
sudo /etc/init.d/apache2 restart


wget http://nl1.php.net/distributions/php-5.3.22.tar.bz2
tar jxf php-5.3.22.tar.bz2
cd php-5.3.22


sudo apt-get build-dep php5 -y
sudo apt-get install libcurl4-dev libfcgi-dev libmhash-dev -y


sudo rm -rf /opt/php53 


./configure --prefix=/opt/php53 --enable-force-cgi-redirect --enable-fastcgi --with-regex=php --enable-calendar --enable-sysvsem --enable-sysvshm --enable-sysvmsg --enable-bcmath --with-bz2 --enable-ctype --with-iconv --enable-exif --enable-ftp --with-gettext --enable-mbstring --with-pcre-regex --enable-shmop --enable-sockets --enable-wddx --with-libxml-dir=/usr --with-zlib --with-openssl=/usr --enable-soap --enable-zip --with-mhash=yes --with-gd --with-pear --with-jpeg-dir=/usr/lib --enable-gd-native-ttf --with-ttf --with-xpm-dir=/usr --with-curl --with-xmlrpc


sudo make


sudo make install


sudo chmod ugo+rX -R /opt/php53/
```

When trying to install libcurl4-dev this error pops up:

[img]http://img855.imageshack.us/img855/3687/screenshotfrom201303070.png[/img]

Anyway on how to solve this?

Thanks in advance.

---

### Post by Mr. ViC on 2013-03-07
Bumping!

---

### Post by Cheesemill on 2013-03-07
Have you done what it suggested?

The libcurl4-dev is a virtual package provided by either libcurl4-nss-dev or libcurl4-gnutls-dev, you need to specify which one to install.

So either
```
 sudo apt-get install libcurl4-nss-dev
```
or
```
 sudo apt-get install libcurl4-gnutls-dev
```
depending on which version you want.

---

