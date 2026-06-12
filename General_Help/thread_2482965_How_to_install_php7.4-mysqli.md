---
title: "How to install php7.4-mysqli ?"
date: 2023-01-16
forum: General Help
---

### Post by satimis on 2023-01-16
Hi all,

Ubuntu 22.04

I follow below document to install LAMP stack
How to Install LAMP Stack on Ubuntu 22.04 Server/Desktop
[https://www.linuxbabe.com/ubuntu/install-lamp-stack-ubuntu-22-04-server-desktop](https://www.linuxbabe.com/ubuntu/install-lamp-stack-ubuntu-22-04-server-desktop)

I need php 7.4 there I follow below document to install it without installing php 8.1
How to Install PHP 7.4 on Ubuntu 22.04 LTS
[https://www.linuxcapable.com/how-to-install-php-7-4-on-ubuntu-22-04-lts/](https://www.linuxcapable.com/how-to-install-php-7-4-on-ubuntu-22-04-lts/)

But I need mysql extension
Support for PHP mysqli extension therefore on Terminal;
$ sudo apt-get install php7.4-mysqli ```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'php7.4-mysql' instead of 'php7.4-mysqli'
....
....

```
I can't install 'php7.4-mysqli'

Please help.  Thanks

Regards

---

### Post by deadflowr on 2023-01-16
Sure it's not provided by the package php7.4-mysql?
Look at
```
apt show php7.4-mysql
```
see if there is a line that says Provides:

if it's listed in the Provides line then the package is builtin.
otherwise known as a virtual package.

---

### Post by satimis on 2023-01-16
> **deadflowr said:**
> Sure it's not provided by the package php7.4-mysql?
Look at
```
apt show php7.4-mysql
```
see if there is a line that says Provides:

if it's listed in the Provides line then the package is builtin.
otherwise known as a virtual package.
Hi.

Thanks for your advice.

It is quite strange to me.

If following below document to install LAMP stack, also install PHP 7.4 not 8.1, I can install php7.4-mysqli

How To Install Linux, Apache, MySQL, PHP (LAMP) Stack on Ubuntu 22.04
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04)

$ apt show php7.4-mysql | grep php7.4```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Package: php7.4-mysql
Source: php7.4
Provides: php-mysqli, php-mysqlnd, php-pdo-mysql, php7.4-mysqli, php7.4-mysqlnd, php7.4-pdo-mysql
Depends: php-common (>= 1:81~), ucf, php7.4-common (= 1:7.4.33-3+ubuntu22.04.1+deb.sury.org+1), libc6 (>= 2.15)

```

Now I can't install php-7.4-mysqli

$ apt show php7.4-mysql | grep php7.4-mysqli```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Provides: php-mysqli, php-mysqlnd, php-pdo-mysql, php7.4-mysqli, php7.4-mysqlnd, php7.4-pdo-mysql

```

The only difference is now running mariadb not mysql ?

Regards

---

