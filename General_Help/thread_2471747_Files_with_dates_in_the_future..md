---
title: "Files with dates in the future."
date: 2022-02-08
forum: General Help
---

### Post by georgesgiralt on 2022-02-08
Hello !
On my laptop I've some files with dates in the future. They are all in the same directory and they belong to journalctl ... So I'm worried. 
```
# touch -d Tomorrow now
# ll now
-rw-r--r-- 1 root root 0 févr.  9  2022 now
# find / -newer now -print 2>/dev/null | xargs ls -lh
-rw-r-----+ 1 root systemd-journal 8,0M mai   18  2088 /var/log/journal/2a10bb83db694c868f722218c37d6fe3/system@f241a697459742358ba01f4a7fbca51e-0000000000018e1a-000ef406ad84236a.journal
-rw-r-----+ 1 root systemd-journal 8,0M mai   18  2068 /var/log/journal/2a10bb83db694c868f722218c37d6fe3/system@f241a697459742358ba01f4a7fbca51e-0000000000018e1c-000d45a43cb05073.journal
-rw-r-----+ 1 root systemd-journal 8,0M mai   18  2051 /var/log/journal/2a10bb83db694c868f722218c37d6fe3/user-1000@874c4d66e0da470680d76f9e77d2e809-0000000000018e1d-000b079cb5e8d83a.journal
#
```
I've looked into one and got : 
```
# journalctl --file=/var/log/journal/2a10bb83db694c868f722218c37d6fe3/user-1000@874c4d66e0da470680d76f9e77d2e809-0000000000018e1d-000b079cb5e8d83a.journal
-- Logs begin at Fri 2068-05-18 21:19:52 CEST, end at Fri 2068-05-18 21:19:52 CEST. --
mai 18 21:19:52 laptop update-notifier.desktop[3005]: /usr/lib/ubuntu-release-upgrader/check-new-release-gtk:30: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version>
mai 18 21:19:52 laptop update-notifier.desktop[3005]:   from gi.repository import Gtk
mai 18 21:19:52 laptop update-notifier.desktop[3005]: WARNING:root:timeout reached, exiting
#
```

I would be delighted to get your advice about this. 
Many thanks in advance for your help and advice !

---

### Post by Xian on 2022-02-08
It's possible your log files are posting with a different time zone. 

Try a reset:

$ sudo dpkg-reconfigure tzdata
$ sudo service rsyslog restart

Then monitor the subsequent entries.

---

### Post by georgesgiralt on 2022-02-09
Xian, thank you for your answer.
I wonder if the time zone even if wrong is sufficient to explain dates in 2051, 2068 and 2088 !

---

### Post by #&amp;thj^% on 2022-02-09
> **georgesgiralt said:**
> Hello !
On my laptop I've some files with dates in the future. They are all in the same directory and they belong to journalctl ... So I'm worried. 
```
# touch -d Tomorrow now
# ll now
-rw-r--r-- 1 root root 0 févr.  9  2022 now
# find / -newer now -print 2>/dev/null | xargs ls -lh
-rw-r-----+ 1 root systemd-journal 8,0M mai   18  2088 /var/log/journal/2a10bb83db694c868f722218c37d6fe3/system@f241a697459742358ba01f4a7fbca51e-0000000000018e1a-000ef406ad84236a.journal
-rw-r-----+ 1 root systemd-journal 8,0M mai   18  2068 /var/log/journal/2a10bb83db694c868f722218c37d6fe3/system@f241a697459742358ba01f4a7fbca51e-0000000000018e1c-000d45a43cb05073.journal
-rw-r-----+ 1 root systemd-journal 8,0M mai   18  2051 /var/log/journal/2a10bb83db694c868f722218c37d6fe3/user-1000@874c4d66e0da470680d76f9e77d2e809-0000000000018e1d-000b079cb5e8d83a.journal
#
```
I've looked into one and got : 
```
# journalctl --file=/var/log/journal/2a10bb83db694c868f722218c37d6fe3/user-1000@874c4d66e0da470680d76f9e77d2e809-0000000000018e1d-000b079cb5e8d83a.journal
-- Logs begin at Fri 2068-05-18 21:19:52 CEST, end at Fri 2068-05-18 21:19:52 CEST. --
mai 18 21:19:52 laptop update-notifier.desktop[3005]: /usr/lib/ubuntu-release-upgrader/check-new-release-gtk:30: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version>
mai 18 21:19:52 laptop update-notifier.desktop[3005]:   from gi.repository import Gtk
mai 18 21:19:52 laptop update-notifier.desktop[3005]: WARNING:root:timeout reached, exiting
#
```

I would be delighted to get your advice about this. 
Many thanks in advance for your help and advice !
If you are truly worried might be worth scrubbing your journalctl, and then monitor journalctl again
I must say that is a bit odd having those dates present.
The self maintenance method is to vacuum the logs by size or time.

Retain only the past two days:
```

journalctl --vacuum-time=2d
```

Retain only the past 500 MB:
```

journalctl --vacuum-size=500M
```

**man journalctl** for more information.
You may have already known this I'm guessing

---

