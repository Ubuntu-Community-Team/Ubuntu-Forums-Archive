---
title: "can't install apache2-dev"
date: 2007-09-10
forum: General Help
---

### Post by prickly on 2007-09-10
I am following these instructions: [http://baheyeldin.com/technology/linux/installing-php-apc-on-ubuntu-dapper-and-debian.html](http://baheyeldin.com/technology/linux/installing-php-apc-on-ubuntu-dapper-and-debian.html)

When i enter this command:

**apt-get install apache2-dev php5-dev php-pear make **

I get this message:

[B]package apache2-dev is a virtual package provided by: 
apache2-threaded-dev 2.0.22-4ubuntu2.2 
You should explicitly select one to install. 
E: package apache2-dev has no installation candidate. [/B]

I am using Ubuntu Server 6.06 and have enabled additional repositories ... do i need to enable another repository or something?

Any help is much appreciated.

---

### Post by ruibernardo on 2007-09-10
The apache2-dev is a virtual package. You need to install the package **apache2-threaded-dev** to get apache2-dev installed ([http://packages.ubuntu.com/dapper/virtual/apache2-dev](http://packages.ubuntu.com/dapper/virtual/apache2-dev)). 

The site  [packages.ubuntu.com]("http://packages.ubuntu.com") has a list of all the packages on the official repos. In case of doubt, you can search there.

---

### Post by prickly on 2007-09-10
thanks very much for the reply - much appreciated.

---

