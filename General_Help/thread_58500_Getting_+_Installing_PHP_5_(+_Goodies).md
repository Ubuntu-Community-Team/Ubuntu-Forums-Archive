---
title: "Getting + Installing PHP 5 (+ Goodies)"
date: 2005-08-20
forum: General Help
---

### Post by Freddie on 2005-08-20
Hi, I have just installed Apache 2 and would like to install PHP 5. However, I could not find anything in my respositories (I have added the extra ones). I want to install PHP 5 along with MySQL (with support for PHP) as well as all of the normal modules/extensions which I have come to expect (Curl, SQLite, FTP, Zlib, BZ2 etc). Can anyone tell me what I need to do?

I am on Mac PPC btw.

---

### Post by Freddie on 2005-08-21
I have looked at the PHP 5 install guide (on this forum) but it has not seemed to work as when I added the repositiories I got 404 errors when I tried to update by cache.

---

### Post by aouie on 2006-02-01
I am now using Dotdeb packages for PHP5 with Kubuntu 5.10 (Breezy). Dotdeb finally got all the things I wanted for PHP5 and Apache 1.3. They recently got the pdo support going. They also have pear, mysql, pgsql, ....
deb [http://packages.dotdeb.org/](http://packages.dotdeb.org/) stable all
deb-src [http://packages.dotdeb.org/](http://packages.dotdeb.org/) stable all
Sincerely,
Aouie

---

### Post by moreweb on 2006-06-22
Hi! 
I'm want have PDO support with PHP5 also.
But if I try to add this line on in my ubuntu **/etc/apt/sources.list** apt ignore the server: ```
...
Ign http://packages.dotdeb.org stable Release.gpg                             
Hit http://security.ubuntu.com dapper-security/restricted Sources             
Hit http://it.archive.ubuntu.com dapper-updates/main Sources
Hit http://it.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://packages.dotdeb.org stable Release        
Ign http://packages.dotdeb.org stable/all Packages
Ign http://packages.dotdeb.org stable/all Sources
...

```

There is a way to use debian repository?

Thanks! :D

[EDIT]
But if I try and **sudo apt-cache search pdo** I found the *php5-pdo-** packages from dotdeb. I can use the these?

---

