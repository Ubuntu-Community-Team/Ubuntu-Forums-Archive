---
title: "MySQL problems"
date: 2004-11-24
forum: General Help
---

### Post by herweg on 2004-11-24
Has anyone been able to get MySQL running with PHP using the packages in the repositories? I can't seem to get them working together. I get an error that PHP doesn't recognize mysql_connect(). I'm running apache2. I also tried compiliing PHP from source, but when I do that, apache doesn't recognize the php, and the browser asks me to download it. Any ideas?

---

### Post by dataw0lf on 2004-11-24
I've gotten it working just fine (but not with Apache 2).  It could be a problem with Apache 2, Zend has already stated that PHP has been acting funky with it.  
dataw0lf

---

### Post by jysse on 2004-11-24
Same kind of problem here. I did uncomment line "extension=mysql.so" on php.ini
Php works when try a test page.

I get this error:

Fatal error: Call to undefined function: mysql_connect() ...

Anyone care to help ?

---

### Post by jysse on 2004-11-25
I've done it.

Reason for mysql not working was because of a missing php4-mysql package.

Could not find it with apt. I had to add "universe" repository to sources.lst.

After that "apt-get install php4-mysql" solved it.

Look at HOWTO: Enabling the Universe APT repository

jysse

---

