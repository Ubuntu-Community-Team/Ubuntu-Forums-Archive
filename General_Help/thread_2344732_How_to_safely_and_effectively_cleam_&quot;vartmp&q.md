---
title: "How to safely and effectively cleam &quot;/var/tmp&quot; folder"
date: 2016-11-28
forum: General Help
---

### Post by p2bc on 2016-11-28
Ok back story and setup config:

I have my /usr, /var, /tmp, and so on on separate partitions, old school, and for every iteration of install these partitions have gone unchanged in their sizes. Just the occasion format with any new LTS fresh install release. I did a install in June with 16.04 with no hiccups what so ever.

Recently, two to three weeks, I have been warnings that my /var is full. Now in the past I would use my machine to test for php websites, I even had 3 full versions of Drupal 8 when it was in beta installed in my /var/www folder, along with about another hundred php files, and I never got a warning that my /var folder was full. Point beine, that was when I was actively putting stuff in my /var director. So you could understand my confusion for my recent warnings.

So I did a "du" command to see the trouble spot and got:

```

sudo du -sxhc /var/*
6.3M    /var/backups
128M    /var/cache
640K    /var/crash
849M    /var/lib
4.0K    /var/local
0    /var/lock
20M    /var/log
16K    /var/lost+found
4.0K    /var/mail
4.0K    /var/metrics
4.0K    /var/opt
0    /var/run
40K    /var/snap
128K    /var/spool
2.5G    /var/tmp
36K    /var/www
3.5G    total

```

The tmp folder is taking over two thirds the partition, so I did a few searches, and found nothing current, 2012, let alone relevant.

So I ask, what would be a safe and effective way to clear the /var/tmp folder.
Also what could be the cause, just for future problem solving. 
I did play with snappy a month ago, nothing serious, just install the equivalent of "Hello World", anyways was wondering if that could be the culprit causing the bloat?

Thanks in advance

---

### Post by wildmanne39 on 2016-11-28
Thread closed. Duplicate post here:
[https://ubuntuforums.org/showthread.php?t=2344719](https://ubuntuforums.org/showthread.php?t=2344719)

---

