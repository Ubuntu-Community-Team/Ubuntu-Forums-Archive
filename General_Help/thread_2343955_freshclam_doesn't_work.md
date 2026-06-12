---
title: "freshclam doesn't work"
date: 2016-11-21
forum: General Help
---

### Post by lukas34 on 2016-11-21
when using freshclam I get this error messages:
```
ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!).
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).

```
ld/ls:
```

drwxr-xr-x 2 clamav vhost 4096 Nov 21 06:25 /var/log/clamav
-rw-r----- 1 clamav vhost 4520 Nov 21 10:48 /var/log/clamav/freshclam.log
```
where vhost is the gourp in which user www-data and my sudouser is
I already restarted freshclam daemon and my server

---

### Post by speartip on 2016-11-21
Think I've had a similar problem before. Try:
```
sudo rm /var/log/clamav/freshclam.log && sudo freshclam
```

---

### Post by lukas34 on 2016-11-21
worked! thx!

---

### Post by speartip on 2016-11-21
No problem.

---

### Post by ajgreeny on 2016-11-21
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

