---
title: "sbackup just keeps running until space runs out"
date: 2007-09-03
forum: General Help
---

### Post by Sefianix on 2007-09-03
I've installed sbackup (and I have other machines that I've installed on and it works fine; dapper, feisty).  When I run it and it tries to do it's first (full) backup, it just keeps running until i run out of space.  I don't know what to do; I've reinstalled multiple times (using 'comple removal'), I've set it to only backup /home.  No matter what I do; it just eats up disk space.  This is a feisty install with the standard package (v. 0.10.3-0.1).  I've tried opening the tgz file within the backup directory sbackup creates but it fails b/c it's not complete.  I've also tried looking at log files but I guess sbackup doesn't log stuff.  Is there some kind of commandline thing I can do to get a better idea of what is screwing up sbackup??  I was wondering if there was some kind of circular reference with a soft link somewhere; it's just a guess since it just keeps going as if there's no end to the files it's trying to backup.  Help please!

here is my sbackup.conf file:
```

[exclude]
regex = \.mp3,\.avi,\.mpeg,\.mpg,\.mkv,\.ogg,\.ogm,\.tmp,/home/[^/]+?/\.thumbnails/,/home/[^/]+?/\.Trash,/home/.mozilla/.+/Cache/
maxsize = 100000000

[places]
prefix = /usr

[dirconfig]
/tmp = 0
/proc = 0
/home = 1
/dev = 0
/var/cache = 0
/var/tmp = 0
/sys = 0

[general]
purge = log
maxincrement = 21
lockfile = /var/lock/sbackup.lock
target = /backups/dailyBackups
format = 1

```

Note: the target is a (2nd drive) partition mounted to /backups; however, I don't believe this is a problem b/c I've also tried the default location /var/backup and it still has the same problem.

---

