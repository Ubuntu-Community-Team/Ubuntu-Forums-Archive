---
title: "Phpize: Cannot find build files at ...."
date: 2018-09-10
forum: General Help
---

### Post by vincej on 2018-09-10
Using Ubuntu 16.04. I was installing xdebug. However, I forgot I had an old version of PHP 7.0 still present in the file system, although not being use. So, phpize did it's work in the old php 7.0 folder and not in my current php7.2 folder. Seeing the mistake I deleted the 7.0 files, and reran phpize expecting it to load my 7.2 folder with xdebug. However, now it gives me an error: "Can not find build files at '/usr/lib/php/20151012/build'. Please check your PHP installation." 

Well, I checked my loaded php.ini and there is no mention of this file. Moreover, the "20151012" folder belonged to the 7.0 install. I am now using 20170829 for all my extensions. 

How to get rid of this error message? How do I get phpize to see my 7.2 folders?

Many thanks !!

---

