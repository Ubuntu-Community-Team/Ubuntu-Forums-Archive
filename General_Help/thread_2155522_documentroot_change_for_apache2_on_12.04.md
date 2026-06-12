---
title: "documentroot change for apache2 on 12.04"
date: 2013-06-18
forum: General Help
---

### Post by enienws on 2013-06-18
Hello folks,

I have been trying to change DocumentRoot for apache2 on my system without success. 

I know that apache is running with a user www-data which is in www-data group. I have modified sites-available file such that DocumentRoot is not pointing to /home/adoniss/www. 

But when I try to access an html page under that folder, a 403 error is generated. In order to solve that problem I have added www-data to adoniss group. 

Access privileges for adoniss root folder seems like following: 

```
drwxr-x--- 25 adoniss adoniss 4096 Jun 18 20:42 adoniss
```

and /adoniss/www privileges seems like following:

```
drwxr-xr-x 2 adoniss adoniss 4096 Jun 18 20:06 www
```

I think with these credentals given to adoniss group should be fine to solve 403 problem. But the problem is still continuing

Any suggesstions?

Thanks in advance.

---

### Post by linuxtechguy on 2013-06-18
Check parent folder permissions

---

