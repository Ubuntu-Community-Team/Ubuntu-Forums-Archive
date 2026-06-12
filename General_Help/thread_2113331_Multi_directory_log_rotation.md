---
title: "Multi directory log rotation"
date: 2013-02-07
forum: General Help
---

### Post by mahi_nix on 2013-02-07
Hi Folks,
 
I have Ubuntu 12.10 (quantal) as web server and i have hosted so many sites on the server now i watned to rotate all my web sites Debug.log files which are in their separate directories. the name of the directories are on numbers. Please check below for reference.
 
/srv/www/static/sites/601961/logs/debug.log 
/srv/www/static/sites/601962/logs/debug.log 
/srv/www/static/sites/601963/logs/debug.log 
/srv/www/static/sites/601964/logs/debug.log 
/srv/www/static/sites/601965/logs/debug.log 
 
I have approx 1400 directories which has debug.log giles in its "logs" directories. now i watned to rotate this log files in single configuration and for that i done the below configurations.
 
>  
/srv/www/static/sites/*/logs/debug.log {
daily
rotate 14
compress
notifempty
create 0640 www-data www-data
postrotate
[ ! -f /var/run/nginx.pid ] || kill -USR1 `cat /var/run/nginx.pid`
endscript
}

 
I tested the configurations through below command:
 
logrotate -d /etc/logrotate.d/debug-catalog
 
The results shows it is rotating the files but when i am checking into the directories i could not found any rotation.
 
Please help me to resolve the issue or suggest me the script to rotate the files.
 
Thank You in Advance,
 
Regards,

---

### Post by mahi_nix on 2013-02-07
Hi Friends,

Anyone can Please suggest me the solution on multi directory log rotation.

Thanks in advance,

Regards,

---

