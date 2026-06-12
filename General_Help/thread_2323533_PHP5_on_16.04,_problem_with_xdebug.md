---
title: "PHP5 on 16.04, problem with xdebug"
date: 2016-05-06
forum: General Help
---

### Post by bluepicaso2 on 2016-05-06
So i had to install php 5.6 on my system since the project we are working on uses php 5.
So everything seems to work fine except whenever i do a ```
apt-get install
```
i see this error in middle of installation
```

Setting up php5-xdebug (2.3.3-1ubuntu1) ...
/var/lib/dpkg/info/php5-xdebug.postinst: 11: /var/lib/dpkg/info/php5-xdebug.postinst: php5enmod: not found
dpkg: error processing package php5-xdebug (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 php5-xdebug

```

can someone help me resolve it

---

### Post by matt_symes on 2016-05-06
Hi

php5enmod looks to be in the php5-common package.

```
matthew-xu-16-04:/home/matthew:0 % apt-file search php5enmod
php5-common: /usr/sbin/php5enmod
matthew-xu-16-04:/home/matthew:0 % 
```

You have installed that package ?

```
apt-cache policy php5-common
```

The file exists ?

```
file /usr/sbin/php5enmod
```

Your path is correct ?

```
echo $PATH
```

Kind regards

---

### Post by bluepicaso2 on 2016-05-06
i simply removed **php5-xdebug** and installed **php-xdebug**
It seems to fix issue.
forgot to mention I am on 16.04 where default php is **php7** but I needed php5.

---

