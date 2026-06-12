---
title: "Gallery2 exceed max file size"
date: 2007-07-11
forum: General Help
---

### Post by gargo2000 on 2007-07-11
Gallery version 2
PHP version 5.1.2
Webserver Apache2 2.0.55
Database MySQL 5.0.22
Activated toolkits NetPbm, Dcraw, Ffmpeg, ImageMagick
Operating system Ubuntu 6.06 LTS
Browser Firefox 1.5.0.12

I have uploaded several albums, but now I am not able to upload any more to my server Gallery2. I receive the following message:

There was a problem processing your request, see below for details.
Input file DSC_9577.JPG exceeds maximum permitted file size

My thoughts were that there is a specific amount of space available in the Gallery2 settings and I am unable to find it to change. Please let me know your thoughts on this topic.

---

### Post by Mr. C. on 2007-07-11
There are two configuration variables I can think of that will cause this:

In your php.ini file (probably in /etc/php.ini), make sure your post_max_size variable is larger than your maximum expected upload:

```
post_max_size = 20M
```

In apache's php.conf file, raise the size of LimitRequestBody:

```
LimitRequestBody 20971520
```

```
locate php.conf
locate php.ini
```

to find them.  Reload apache after changes.

MrC

---

### Post by gargo2000 on 2007-07-11
> **Mr. C. said:**
> There are two configuration variables I can think of that will cause this:

In your php.ini file (probably in /etc/php.ini), make sure your post_max_size variable is larger than your maximum expected upload:

```
post_max_size = 20M
```



I have completed this.

The next part using "locate php.conf" I cant do there is no file.  I did find one for PHP5.CONF though, but did not have the following in it.

> 
In apache's php.conf file, raise the size of LimitRequestBody:

```
LimitRequestBody 20971520
```

MrC

The PHP5.CONF was located in 2 places: 
/etc/apache2/mods-enabled/php5.conf
/etc/apache2/mods-available/php5.conf

---

### Post by Mr. C. on 2007-07-11
The file /etc/apache2/mods-enabled/php5.conf would be the correct file.  Add the variable and set it to your desired size, and restart apache.

MrC

---

