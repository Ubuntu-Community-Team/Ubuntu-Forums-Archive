---
title: "How safe is it to remove old files from /var/log/?"
date: 2006-08-08
forum: General Help
---

### Post by kpkeerthi on 2006-08-08
Just noticed about 34 files hanging around in /var/log/ folder. Can these be removed safely? 

```

>>:/var/log$ ls -l *.gz
-rw-r----- 1 root adm    2000 2006-08-06 11:10 acpid.1.gz
-rw-r----- 1 root adm    1834 2006-07-30 10:00 acpid.2.gz
-rw-r----- 1 root adm    1500 2006-07-23 15:42 acpid.3.gz
-rw-r----- 1 root adm    1306 2006-07-16 11:03 acpid.4.gz
-rw-r--r-- 1 root root   8457 2006-08-01 17:39 aptitude.1.gz
-rw-r----- 1 root adm   15523 2006-07-26 18:26 auth.log.1.gz
-rw-r----- 1 root adm    4152 2006-07-19 18:00 auth.log.2.gz
-rw-r----- 1 root adm    6942 2006-07-12 18:51 auth.log.3.gz
-rw-r----- 1 root adm   82601 2006-07-30 10:04 daemon.log.1.gz
-rw-r----- 1 root adm   10506 2006-07-26 18:27 daemon.log.2.gz
-rw-r----- 1 root adm    8667 2006-07-19 18:02 daemon.log.3.gz
-rw-r----- 1 root adm    1001 2006-07-05 22:02 daemon.log.4.gz
-rw-r----- 1 root adm   12482 2006-07-26 18:27 debug.1.gz
-rw-r----- 1 root adm    6365 2006-07-19 17:54 debug.2.gz
-rw-r----- 1 root adm   25787 2006-07-12 18:51 debug.3.gz
-rw-r----- 1 root adm   51059 2006-08-02 17:33 kern.log.1.gz
-rw-r----- 1 root adm  203738 2006-07-31 18:20 kern.log.2.gz
-rw-r----- 1 root adm  184003 2006-07-26 18:27 kern.log.3.gz
-rw-r----- 1 root adm   83840 2006-07-19 17:53 kern.log.4.gz
-rw-r----- 1 root adm  223163 2006-07-08 11:31 kern.log.5.gz
-rw-r----- 1 root adm   15698 2006-08-02 17:42 messages.1.gz
-rw-r----- 1 root adm  211904 2006-08-01 17:41 messages.2.gz
-rw-r----- 1 root adm  160637 2006-07-26 18:28 messages.3.gz
-rw-r----- 1 root adm   74116 2006-07-19 18:03 messages.4.gz
-rw-r----- 1 root adm  197297 2006-07-08 11:36 messages.5.gz
-rw-r----- 1 root adm   79000 2006-08-06 11:16 syslog.1.gz
-rw-r----- 1 root adm   60852 2006-08-04 18:37 syslog.2.gz
-rw-r----- 1 root adm  117393 2006-08-03 19:26 syslog.3.gz
-rw-r----- 1 root adm   33750 2006-08-02 17:38 syslog.4.gz
-rw-r----- 1 root adm   55823 2006-08-01 17:41 syslog.5.gz
-rw-r----- 1 root adm   81306 2006-07-31 18:25 syslog.6.gz
-rw-r----- 1 root adm    4290 2006-07-26 18:26 user.log.1.gz
-rw-r----- 1 root adm    2263 2006-07-19 17:54 user.log.2.gz
-rw-r----- 1 root adm   10206 2006-07-12 18:54 user.log.3.gz

>>:/var/log$ ls -l *.gz | wc -l
34

```

---

### Post by GrumpySmurf on 2006-08-08
Sure you can remove them if filesystem space is scarce and you dont care about old log messages.

You can also specify different archiving options of rotated logs by editting /etc/logrotate.conf.

```
# keep 4 weeks worth of backlogs
rotate 4
```
Change the 4 to a smaller number. Read the man page on logrotate for more information.

---

### Post by kpkeerthi on 2006-08-08
Great. Thank you.

---

