---
title: "/dev/sda2/ is using up my precious storage and I can'"
date: 2017-05-20
forum: General Help
---

### Post by johnr24 on 2017-05-20
Oops, apparently I can't edit title.

Here's my df -h

```
root@   :~# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            477M     0  477M   0% /dev
tmpfs           100M  5.7M   94M   6% /run
/dev/vda2        50G  4.3G   43G  10% /
tmpfs           497M     0  497M   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           497M     0  497M   0% /sys/fs/cgroup
tmpfs           100M     0  100M   0% /run/user/0

```
I'm running ubuntu on a 50GB VPS and I'm losing 10% of my storage in /dev/vda2. Anyone have an idea on what is using up 4.3G of my storage?

---

### Post by deadflowr on 2017-05-20
> I'm running ubuntu on a 50GB VPS and I'm losing 10% of my storage in /dev/vda2. Anyone have an idea on what is using up 4.3G of my storage?

the operating system

---

### Post by Bashing-om on 2017-05-20
johnr24; Hello - Welcome to the forum.

'ncdu' is handy for finding what's using space on any device:
What shows :
```

ncdu -x /

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2017-05-20
> **deadflowr said:**
> the operating system
+1
> **Bashing-om said:**
> johnr24; Hello - Welcome to the forum.

'ncdu' is handy for finding what's using space on any device:
What shows :
```

ncdu -x /

```
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]

Nice little tool B-om...learn something new every day.  :D
Sorry off topic just driving by. ;)

---

