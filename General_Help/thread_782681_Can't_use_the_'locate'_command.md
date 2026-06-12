---
title: "Can't use the 'locate' command"
date: 2008-05-05
forum: General Help
---

### Post by Bucephalus01 on 2008-05-05
Hi

I'm following the work instructions to install apache, php and mysql at 
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

In the "Edit PHP Configuration to Work With MYSQL (Ubuntu Dapper)" section
it says to use locate to find the mysql.so file.

When I try this I get this error. 

locate: can not open `/var/lib/mlocate/mlocate.db': No such file or directory

Does anybody know what this means or how I can get 'locate' operational?
Cheers
Bucephalus

---

### Post by ad_267 on 2008-05-05
This is just a guess but try entering
```
sudo updatedb
```
then try again.

---

### Post by Bucephalus01 on 2008-05-05
That worked, thanks.

---

