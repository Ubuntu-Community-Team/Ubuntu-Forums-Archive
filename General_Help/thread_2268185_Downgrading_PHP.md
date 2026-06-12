---
title: "Downgrading PHP"
date: 2015-03-06
forum: General Help
---

### Post by musicweb on 2015-03-06
We installed 14.04 with LAMP, which has PHP 5.5.9 
If we remove the LAMP stack, what are the consequences?
Will mysql databases be deleted also, along with our virtual hosts?
We need PHP 5.4 or below to run some new software along with
Zend Loader, but Zend doesn't support PHP 5.5 yet.
Aside from re-installing Ubuntu, what are our options?
Tried PHPbrew, but we get "Configure failed" every time we try
to install a different PHP version.

We found the following post, but it doesn't say anything about
removing mysql, only installing it.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge `dpkg -l | grep php | grep -w 5.5 | awk '{print $2}' | xargs`
sudo apt-get purge apache2 php5 libapache2-mod-php5
sudo sed -i.bak "s/trusty/precise/g" /etc/apt/sources.list
sudo apt-get update
sudo apt-get install apache2 apache2-suexec libapache2-mod-fcgid php5-cgi
sudo apt-get install php5-mysql php5-curl php5-gd php5-intl php-pear php5-imagick php5-imap php5-mcrypt php5-memcache php5-ming php5-ps php5-pspell php5-recode php5-sqlite php5-tidy php5-xmlrpc php5-xsl php5-xdebug
sudo sed -i "s/precise/trusty/g" /etc/apt/sources.list
dpkg --get-selections | egrep '^(apache|php)' | sed 's/install/hold/g' | sudo dpkg --set-selections
sudo apt-get update
sudo apt-get install  mysql-client mysql-server phpmyadmin
```

---

### Post by scoon on 2015-03-06
Hey there, 

To see what would get removed, you can use the simulate flag with apt-get, like so: ```
apt-get purge -s php5
```.  This will show what could get removed without actually removing it.

Thanks, 

Skip

---

### Post by musicweb on 2015-03-07
Result:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc-client2007e libicu52 mlock php-auth php-db php-http-request php-mail
  php-mdb2 php-net-dime php-net-smtp php-net-socket php-net-url php-soap
  php5-imap php5-intl php5-pspell php5-sqlite roundcube-mysql tinymce
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  php-auth-sasl* php-log* php-mail-mime* php5* roundcube* roundcube-core*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Purg php-auth-sasl [1.0.6-1]
Purg php-log [1.12.7-1]
Purg roundcube [0.9.5-4]
Purg roundcube-core [0.9.5-4]
Purg php-mail-mime [1.8.8-1]
Purg php5 [5.5.9+dfsg-1ubuntu4.6]

```

So will I be able to get PHP 5.4 and install it without problems?
If yes, where do I get the older versions?

---

### Post by dragonfly41 on 2015-03-07
This may no longer be relevant if you have now purged php 5.5

but one option using PHPFarm is to run different versions of php mapped to different virtualhosts
as explained in these articles ..

[http://thejibe.com/blog/14/02/phpfarm](http://thejibe.com/blog/14/02/phpfarm)

[https://gist.github.com/gmodarelli/5887778](https://gist.github.com/gmodarelli/5887778)

---

### Post by musicweb on 2015-03-07
I have not purged anything yet....
So PHPFarm is a good option here?
Have you any experience with it?

---

### Post by dragonfly41 on 2015-03-07
It is good only if you need to switch between PHP versions.
But if you only need one (old) version of PHP it will not help you.
And yes I have tried PHPFarm for development purposes.

Another approach might be to set your path to PHP (5.5 or 5.4) in ~/.profile

e.g. export PATH=${PATH}:"/usr/bin/php5"

---

