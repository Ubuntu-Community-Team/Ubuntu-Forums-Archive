---
title: "recover database"
date: 2014-06-04
forum: General Help
---

### Post by shree2 on 2014-06-04
Hello,

I had 12.04 running on my laptop, with vTiger CRM on it. The laptop has crashed. I have reinstalled new 12.04 in new partition.

I want to recover database from my old installation. I have access to  all old files  ( /var  etc....)

Is it possible to recover data ? I have searched two old threads but could not find answere.

Please Help..... 

Best Regards,
Shree

---

### Post by TheFu on 2014-06-04
Welcome to the forums.

I haven't run vtiger (or any CRM) in a few years. I recall that it used mysql as the DB, so if you find that set of files and get it working again, you'll be fine.   Of course, having a clean, uncorrupted, backup would be better. Open DB files during a system crash can become corrupt, though most DBMS systems have good protections against that, so it isn't really likely.

I don't know the exact commands to type, sorry. Found this:  [https://stackoverflow.com/questions/484750/restoring-mysql-database-from-physical-files](https://stackoverflow.com/questions/484750/restoring-mysql-database-from-physical-files)  Hope it helps.

---

