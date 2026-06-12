---
title: "InnoDB support missing in MySQL"
date: 2013-02-11
forum: General Help
---

### Post by tvbowman on 2013-02-11
Everything was working fine for weeks. Now, all of a sudden, I get errors on every PHP file in our website, and when I go to MySQL Workbench or phpmyadmin to check the database, it says "#1286 - Unknown storage engine 'InnoDB'"

When I look in MySQL I get the following:

Engine | Support | Comment ...
---------------------------------------------
InnoDB | NO      | Supports Transactions, ...


I have tried renaming the files ib_logfile0 and ib_logfile1 and restarting MySQL, but it does not appear to be creating new log files, so I am not sure what to do.

---

### Post by tvbowman on 2013-02-11
I fixed my own problem. FYI: if you ever lose InnoDB support in MySQL, and you do not know what caused it, look in the /etc/mysql/conf.d/ folder and see if there is something there from a program you may have installed then removed. In my case, I had installed Zentyal-firewall, and removed it soon after, but the zentyal.cnf file was still there, causing InnoDB to be disabled in MySQL. All I had to do was rename that file, and restart the MySQL service, and I am good to go!

):P

---

