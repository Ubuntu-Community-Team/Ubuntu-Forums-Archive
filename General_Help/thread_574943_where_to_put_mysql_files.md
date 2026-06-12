---
title: "where to put mysql files??"
date: 2007-10-13
forum: General Help
---

### Post by Guardian-Mage on 2007-10-13
I had a mysql server setup on windows, then I moved to ubuntu. The path to my mysql installation was E:\webserver\mysql
The only thing I saved was the data folder with all of my databases in it. I saved it to E:/webserver/databases
How can I point mysql in ubuntu to these files or something. I edited the my.cnf file or whatever in /etc/mysql but It only came up with errors.

---

### Post by HermanAB on 2007-10-13
MySQL by default stores schtuff in /var/lib/mysql.  You can put a soft link in there pointing to wherever you put your data.

ln -s wherever/it/is /var/lib/mysql/whatchamacallit

Otherwise, move your data to /var/lib/mysql

Cheers,

Herman

---

