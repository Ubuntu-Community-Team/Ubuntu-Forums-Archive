---
title: "Rights for /var"
date: 2014-04-06
forum: General Help
---

### Post by Jeroen De Dauw on 2014-04-06
I accidentally ended up running "sudo chown root /var -R", and now I can no longer login. Still getting the full disk encryption password step, though not the one after that. To fix the issue, I need to know where the owner cannot be root, so I can change it back.

---

### Post by Elfy on 2014-04-06
This is what I've got 

```
drwxr-xr-x 13 root root     4096 Feb 19 09:59 .
drwxr-xr-x 27 root root     4096 Apr  6 15:34 ..
drwxr-xr-x  2 root root     4096 Apr  5 08:48 backups
drwxr-xr-x 19 root root     4096 Feb 27 13:15 cache
drwxrwsrwt  2 root whoopsie 4096 Apr  6 09:36 crash
drwxr-xr-x 74 root root     4096 Mar 31 07:36 lib
drwxrwsr-x  2 root staff    4096 Jan  6 14:25 local
lrwxrwxrwx  1 root root        9 Feb 20 06:48 lock -> /run/lock
drwxrwxr-x 13 root syslog   4096 Apr  6 15:39 log
drwxrwsr-x  2 root mail     4096 Feb 19 09:50 mail
drwxrwsrwt  2 root whoopsie 4096 Feb 19 09:55 metrics
drwxr-xr-x  2 root root     4096 Feb 19 09:50 opt
lrwxrwxrwx  1 root root        4 Feb 20 06:48 run -> /run
drwxr-xr-x  9 root root     4096 Feb 20 07:12 spool
drwxrwxrwt  2 root root     4096 Apr  6 15:42 tmp

```

---

### Post by Jeroen De Dauw on 2014-04-06
It's all root on my box. Though it does not have the entries where you do have something different to begin with - this is a recent install (13.10).

---

### Post by steeldriver on 2014-04-06
I would suspect your (GUI) login problems are due to the /var/lib/lightdm subdirectory (which needs to be owned by lightdm:lightdm)

```

$ sudo find /var -maxdepth 3 -type d ! \( -uid 0 -o -gid 0 \) -ls
785121    4 drwxr-s---   2 mysql    adm          4096 Oct 12 07:40 /var/log/mysql
 20331    4 drwxrwx--T   2 daemon   daemon       4096 Feb 23 08:48 /var/spool/cron/atspool
 20330    4 drwxrwx--T   2 daemon   daemon       4096 Feb 23 08:48 /var/spool/cron/atjobs
 20329    4 drwxr-xr-x   2 syslog   adm          4096 Mar 30  2012 /var/spool/rsyslog
814554    4 drwxr-xr-x   3 www-data www-data     4096 Mar 31 17:24 /var/cache/apache2
814555    4 drwxr-xr-x   2 www-data www-data     4096 Jul 12  2013 /var/cache/apache2/mod_disk_cache
784909    4 drwx------   5 mysql    mysql        4096 Sep 28  2013 /var/lib/mysql
784985    4 drwx------   2 mysql    mysql        4096 Jul 26  2013 /var/lib/mysql/mysql
922214    4 drwx------   2 mysql    mysql        4096 Oct 18 18:34 /var/lib/mysql/test
784889    4 drwx------   2 mysql    mysql        4096 Jul 26  2013 /var/lib/mysql/performance_schema
797265    4 drwxr-xr-x   2 avahi-autoipd avahi-autoipd     4096 Feb 23  2013 /var/lib/avahi-autoipd
797280    4 drwxrwsr-x   2 libuuid  libuuid      4096 Apr 23  2012 /var/lib/libuuid
847903    4 drwxr-xr-x   2 postgres postgres     4096 Sep  7  2012 /var/lib/postgresql
797267    4 drwxr-xr-x   2 colord   colord       4096 Aug 19  2012 /var/lib/colord
[B]797281    4 drwxr-x---  10 lightdm  lightdm      4096 Apr  5 10:16 /var/lib/lightdm
148551    4 drwx------   2 lightdm  lightdm      4096 Apr  5 10:11 /var/lib/lightdm/.pulse
148536    4 drwx------   4 lightdm  lightdm      4096 Aug 19  2012 /var/lib/lightdm/.cache
148542    4 drwx------   4 lightdm  lightdm      4096 Aug 19  2012 /var/lib/lightdm/.config
148533    4 drwx------   3 lightdm  lightdm      4096 Aug 19  2012 /var/lib/lightdm/.dbus
148541    4 drwx------   2 lightdm  lightdm      4096 Aug 19  2012 /var/lib/lightdm/.gvfs
148546    4 drwx------   2 lightdm  lightdm      4096 Apr  5 10:11 /var/lib/lightdm/.gconf
148561    4 drwxrwxr-x   3 lightdm  lightdm      4096 Aug 19  2012 /var/lib/lightdm/.local
148576    4 drwx------   3 lightdm  lightdm      4096 Aug 19  2012 /var/lib/lightdm/.nv
[/B]
```

Can you log in to one of the non-GUI virtual terminals (Ctrl-Alt-F2 etc.)?

---

### Post by Elfy on 2014-04-06
so would I - just saw the -R in the chown command ...

---

### Post by Jeroen De Dauw on 2014-04-06
Thanks steeldriver and Elfy! I was able to login and post this message, so problem solved :)

---

### Post by Iowan on 2014-04-06
Tag it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

