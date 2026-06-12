---
title: "Mysql headers"
date: 2012-11-04
forum: General Help
---

### Post by tripialos on 2012-11-04
Greetings

I have install mysql by ubuntu`s repo (apt-get install mysql).

I am trying to compile php --with-mysql  but thing is that i dont know where mysql is installed.

In the past, i used to compile mysql under /usr/local/mysql hence i knew where to point when compiling php.

Any ideas?

Thanks

---

### Post by Cheesemill on 2012-11-04
Is there any reason why you don't just install PHP from the repos as well?

It already has MySQL support.

---

### Post by tripialos on 2012-11-04
> **Cheesemill said:**
> Is there any reason why you don't just install PHP from the repos as well?

It already has MySQL support.

I did not because I was thinking that I also need to add php modules on my Apache. I know that this can be added while compiling php.

--with-apxs2=/usr/local/apache2/bin/apxs

So, when you have already compiled apache,  if you install php from repo, will the modules of php added automatically?

---

### Post by Cheesemill on 2012-11-04
Apache in the repos has PHP support.

If all you are trying to do is set up a LAMP server (Linux, Apache, MySQL, PHP) then it can be done with one command, there is no reason to compile anything from source.

```
sudo apt-get install lamp-server^
```
This will install the following packages which should be everything you need.
```
apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.5 mysql-common mysql-server mysql-server-5.5 php5-common php5-mysql
```

---

