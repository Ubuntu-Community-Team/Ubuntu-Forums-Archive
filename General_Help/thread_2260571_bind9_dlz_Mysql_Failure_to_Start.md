---
title: "bind9_dlz Mysql Failure to Start"
date: 2015-01-12
forum: General Help
---

### Post by theonlytalkinggoat on 2015-01-12
I am setting up my first bind9 dlz server, with mysql and I can't get it to start. I followed the directions, here:

[http://ubuntuforums.org/showthread.php?t=1867237](http://ubuntuforums.org/showthread.php?t=1867237)

As far as I can tell, I am not running chrooted and replacing the  names in named.conf with that of my server doesn't work. When I try to launch the  bind9 server, I get:

```
Jan 12 22:31:21 ubuntu named[5860]: generating session key for dynamic DNS
Jan 12 22:31:21 ubuntu named[5860]: sizing zone task pool based on 0 zones
Jan 12 22:31:21 ubuntu named[5860]: Loading 'Msql zone' using driver mysql
Jan 12 22:31:21 ubuntu named[5860]: mysql driver failed to create database connection after 4 attempts
Jan 12 22:31:21 ubuntu named[5860]: SDLZ driver failed to load.
Jan 12 22:31:21 ubuntu named[5860]: DLZ driver failed to load.
Jan 12 22:31:21 ubuntu named[5860]: loading configuration: failure
Jan 12 22:31:21 ubuntu named[5860]: exiting (due to fatal error)
```

named.conf:
```
dlz "Msql zonev" {
   database "mysql
   {host=127.0.0.1 port=3306 dbname=bind9_dlz user=root password=#password}
   {SELECT zone FROM dns_records WHERE zone = '$zone$'}
   {SELECT ttl, type, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'), dat$
    FROM dns_records
    WHERE zone = '$zone$' AND host = '$record$' AND type <> 'SOA' AND type <> '$
   {SELECT ttl, type, data, primary_ns, resp_person, serial, refresh, retry, ex$
    FROM dns_records
    WHERE zone = '$zone$' AND (type = 'SOA' OR type='NS')}
   {SELECT ttl, type, host, mx_priority, IF(type = 'TXT', CONCAT('\"',data,'\"'$
    FROM dns_records
    WHERE zone = '$zone$' AND type <> 'SOA' AND type <> 'NS'}
   {SELECT zone FROM xfr_table where zone='$zone$' AND client = '$client$'}";
};
```

Mysql Version 5.5.40-0ubuntu0.14.04.1
Named Version : 9.9.5-3ubuntu0.1-Ubuntu

There is no firewall and apparmor is uninstalled. 

Can't figure out why bind won't run and I have been pouring over every website I can find, for two days. [URL="http://ubuntuforums.org/showthread.php?t=1867237"]
[/URL]

---

