---
title: "Apache php 'n mysql"
date: 2005-10-12
forum: General Help
---

### Post by eldiablo on 2005-10-12
Hi everyone,
i'm seriously new to linux, 
i want to get a test server running offline

does ubuntu install apache? php or mysql? by default
or do you have to install it your self?

if apache is installed by default how do i start it up or test its running??

thanx

---

### Post by adwait on 2005-10-12
Apache2 is installed. You can start it using
```
sudo /etc/init.d/apache2 start 
```

PHP and MYSQL are not installed bu default, so you will have to install them manually.

---

### Post by eldiablo on 2005-10-14
Thanks is there a tut som where to walk through installing extra apps on ubuntu, 
and what will my localhost be when apache in running?

thanks

---

### Post by tats on 2005-10-14
check out [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

localhost = 127.0.0.1

browse to [http://localhost](http://localhost) once apache is running

---

