---
title: "REALLY screwewd up mysql installation"
date: 2017-10-19
forum: General Help
---

### Post by rebeltaz on 2017-10-19
So. On my old computer, running Ubuntu 10.04, I had MySQL installed acting as a database server for Kodi. My new computer, I installed 16.04 and tried to migrate the database using the advice here - [https://ubuntuforums.org/showthread.php?t=2374652](https://ubuntuforums.org/showthread.php?t=2374652). That's when things went sideways.

When I imported the database, it complained the the user 'kodi' wasn't valid. I had thought the backup would recreate the users, but I guess not. So I dropped the databases and tried to create the user. It complained that the databases were corrupt. So I purged MySQL and resinstalled it. I created the user first - as per [http://kodi.wiki/view/MySQL/Setting_up_MySQL](http://kodi.wiki/view/MySQL/Setting_up_MySQL) - and the import seemed to go ok. Only Kodi couldn't/wouldn't see it. Trying to log back in to MySQL, I kept getting this error - "ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO) - so I tried the steps outlined here - [https://superuser.com/questions/603026/mysql-how-to-fix-access-denied-for-user-rootlocalhost](https://superuser.com/questions/603026/mysql-how-to-fix-access-denied-for-user-rootlocalhost) - and now I cannot get into MySQL at all. 

I don't know if it matters, but I didn't set a root password when I installed MySQL and I never could run 'mysql -u root' without running it as 'sudo mysql -u root'.

How do I COMPLETELY remove MySQL, including all databases, tables, settings, etc - reinstall it and avoid this trouble in the future.

---

