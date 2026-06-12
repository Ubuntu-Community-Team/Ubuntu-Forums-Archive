---
title: "SugarCRM Failure after MySQL updates"
date: 2008-03-21
forum: General Help
---

### Post by mamnmamn on 2008-03-21
Hi,

I installed SugarCRM a few weeks agao and all worked well. I installed some updates lastnight and now SugarCRM can not log in. So, when I browse to the sugarcrm index.php page a get an error, before I loging as a user. The error I get is:

Warning: mysqli_connect() [function.mysqli-connect]: (28000/1045): Access denied for user 'sugarcrm '@'HOSTNAME' (using password: YES) in /var/www/SugarCE-Full-5.0.0b/include/database/MysqliManager.php on line 419

Warning: mysqli_close() expects parameter 1 to be mysqli, boolean given in /var/www/SugarCE-Full-5.0.0b/include/database/MysqliManager.php on line 444
Could not connect to server IPADDRESS as sugarcrm .Access denied for user 'sugarcrm '@'HOSTNAME' (using password: YES)

The MySQL Database does not have a 'sugarcrm '@'HOSTNAME' user, only @localhost and @IPADDRESS.

I SugarCE-Full-5.0.0b/config.php it is listed as the server ip address;

'db_host_name' => 'IPADDRESS',

I have tried to create a 'sugarcrm '@'HOSTNAME' user with the same password but no luck

I have exported the database so could I run the install again and inport the database during the install. I would prefer to learn what is wrong though.

Please help!!

mamnmamn

---

### Post by mamnmamn on 2008-03-21
Hi, no worries it is sorted.

somehow, in SugarCE-Full-5.0.0b/config.php, there was a space at the end of the user name. The old version of mysql was handling this space but new version failed. 

I have removed the space and sugar works again.

Thanks

---

### Post by mamnmamn on 2008-03-21
Hi,

I fixed this issue. It was due to white space at the end of the username in 'db_user_name' => in SugarCE-Full-5.0.0b/config.php.

Now I can log in and perform most tasks. Yet I can not create a meeting. I get the following error;

Error filling in additional detail fields: Query Failed:SELECT name , assigned_user_id parent_name_owner from prospects where id = ''::MySQL error 1054:

I read this post

[http://www.sugarcrm.com/forums/showthread.php?t=29376](http://www.sugarcrm.com/forums/showthread.php?t=29376)

and tried the solution in the link. I ran mysql_upgrade and it gave th "Duplicate column name" warnings the link said it would, but the error still occurs when creating a meeting.

I am running;

MySQL = 5.0.38-Ubuntu_0ubuntu1.4-log
Ubuntu = 7.04
PHP = PHP Version 5.2.1
Kernel = 2.6.20-16-server #2 SMP Fri Feb 1 03:10:48 UTC 2008 i686

Please Help and thanks,

mamnmamn

---

