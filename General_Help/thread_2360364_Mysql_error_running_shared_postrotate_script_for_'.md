---
title: "Mysql: error running shared postrotate script for '/var/log/mysql.log /var/log/mysql/"
date: 2017-05-03
forum: General Help
---

### Post by wayneli0000 on 2017-05-03
Hi,
Hi, I get error every night:
/etc/cron.daily/logrotate
 error running shared postrotate script for '/var/log/mysql.log /var/log/mysql/*log '

I get the error as an email sent to [EMAIL="root@myweb.com"]root@myweb.com[/EMAIL]. The title of the email is:

test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )


I checked the web, someone suggested to run
  GRANT ALL ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY PASSWORD 'xxxx'
which 'xxxx' is the password in the sudo cat /etc/mysql/debian.cnf. But mysql
says password is invalid.

I checked mysql website. Version 5.7.18 (I use this version) fixed a but related the this error, but that is for RPM package (I use ubuntu).  Bug number is Bug #22322685. I checked the bug, no such bug.

I use Ubuntu 16.4, mysql 5.7.18. 

What is wrong please? Any information would be appreciated. Thanks in advance.

---

