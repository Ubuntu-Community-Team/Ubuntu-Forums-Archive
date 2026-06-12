---
title: "apt-get reinstall configuration files"
date: 2006-11-10
forum: General Help
---

### Post by pzazz on 2006-11-10
Hi,

I am using Ubuntu Dapper.

I have looked around a number of formums, but cant find an answer to this one , although it does not seem like an unusual thing to need to do.

I cant get package configuration files to be re-installed using apt-get, for example, if I do:

$ apt-get install apache2
$ rm -rf /var/www /etc/apache2
$ apt-get --purge remove apache2
$ apt-get install apache2

, the /var/www and /etc/apache2 directories are not re-installed.

I have tried various options for apt-get and dpkg, such as --force-confnew and --reinstall, but to no avail.

Anyone got any ideas? I understand the intent - dont blow away the users configuration files, but there is surely a way to reinstall pristine configuration files for a package?

Cheers,
Dave,

---

### Post by pzazz on 2006-11-10
BTW - have also unsuccessfuly tried
$ dpkg-reconfig apache2 
Dave

---

### Post by pzazz on 2006-11-13
Well, I guess the reason I couldn't find an answer was because it was so obvious. The config files are from the package apache2-common, not apache2, so ...

$ /etc/init.d/apache2 stop
$ apt-get --purge remove apache2-common apache2

Removes all the apache config files.

$ apt-get install apache2

Installs all the config files again.

.. Ah well, it was a Friday.
Dave

---

### Post by elwillow on 2006-12-04
> **pzazz said:**
> Well, I guess the reason I couldn't find an answer was because it was so obvious. The config files are from the package apache2-common, not apache2, so ...

$ /etc/init.d/apache2 stop
$ apt-get --purge remove apache2-common apache2

Removes all the apache config files.

$ apt-get install apache2

Installs all the config files again.

.. Ah well, it was a Friday.
Dave
Thanks a lot... 

That worked on my side... only bad things that that you have to reinstall every depedent package you had install..

bah... it will list the removed package...

thanks again...

it was Monday!!
Mathieu

---

