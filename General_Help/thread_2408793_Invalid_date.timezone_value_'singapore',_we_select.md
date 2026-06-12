---
title: "Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now"
date: 2018-12-23
forum: General Help
---

### Post by edicande0477 on 2018-12-23
Hi all,

I have a problem with my website, which I can login but I can't see any menus appear on the page.
My ubuntu server running 16.04.05 LTS with mysql-server version 14.14 dist 5.7.24

then I check the php error.log in /var/log/apache2/error.logs at below:


```
[Sun Dec 23 06:25:02.383287 2018] [mpm_prefork:notice] [pid 1282] AH00163: Apache/2.4.18 (Ubuntu) mod_fcgid/2.3.9 configured -- resuming normal operations
[Sun Dec 23 06:25:02.383308 2018] [core:notice] [pid 1282] AH00094: Command line: '/usr/sbin/apache2'
[Sun Dec 23 21:30:24.831977 2018] [proxy_fcgi:error] [pid 1748] [client 10.x.x.x:63646] AH01071: Got error 'PHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 35\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 106\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 106\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\n'
[Sun Dec 23 21:30:38.754682 2018] [proxy_fcgi:error] [pid 1750] [client 10.x.x.x:63656] AH01071: Got error 'PHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 35\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 106\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 106\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 158\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 186\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 198\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 198\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 322\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 322\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\n', referer: [http://192.x.x.x/dummy/]("http://192.168.100.182/rwis_dummy/")
[Sun Dec 23 21:30:38.784502 2018] [proxy_fcgi:error] [pid 1750] [client 10.x.x.x:63656] AH01071: Got error 'PHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\n', referer: [http://192.x.x.x/dummy/](http://192.x.x.x/dummy/)
[Sun Dec 23 21:30:38.962143 2018] [proxy_fcgi:error] [pid 1749] [client 10.x.x.x:63666] AH01071: Got error 'PHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\n', referer: [http://192.x.x.x/dummy/](http://192.x.x.x/dummy/)
[Sun Dec 23 21:30:45.572638 2018] [proxy_fcgi:error] [pid 6328] [client 10.x.x.x:63668] AH01071: Got error 'PHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/logoff.php on line 10\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/logoff.php on line 10\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/rwis_dummy/lib/classes/rwisDB.php on line 70\n', referer: [http://192.x.x.x/dummy/](http://192.x.x.x/dummy/)
[Sun Dec 23 21:30:45.623846 2018] [proxy_fcgi:error] [pid 6328] [client 10.x.x.x:63668] AH01071: Got error 'PHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 35\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 106\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/login.php on line 106\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\nPHP message: PHP Warning: date(): Invalid date.timezone value 'singapore', we selected the timezone 'UTC' for now. in /var/www/dummy/lib/classes/rwisDB.php on line 70\n', referer: [http://192.x.x.x/dummy/](http://192.x.x.x/dummy/)
```

From some forum they said to try add the timezone in /etc/mysql/mysql.conf.d/mysqld.cnf
[COLOR=#0000cd]default-time-zone='+08:00'[/COLOR]

I have tried it no the result still same at above

the, tried add the timezone in /etc/php/5.6/cli/php.ini
[COLOR=#0000cd]date.timezone = [/COLOR][COLOR=#0000cd]singapore

[/COLOR]The result also still same the error log.

I also have to set the @@global.time_zone and @@session.time_zone in mysql:

[ATTACH=CONFIG]282011[/ATTACH]

All the task after added I always restart the Apache and the Mysql but I only can login but I still cannot see any menus inside,
the php error log also still same at above.

Please any advise how to resolve it?
much appreciate for any help or input come from you all.

---

### Post by edicande0477 on 2019-01-07
please any help from this forum? :(

---

### Post by Bachstelze on 2019-01-07
[FONT=Monospace]"singapore"[/FONT] is not a valid value for [FONT=Monospace]date.timezone[/FONT]. What you want is

```
date.timezone = "Asia/Singapore"
```

The list of valid timezones is here: [http://php.net/manual/en/timezones.php](http://php.net/manual/en/timezones.php)

---

### Post by edicande0477 on 2019-01-09
[COLOR=#000000]@Bachstelze, thanks a lot for your correction! It solved my problem :)

[/COLOR]

---

