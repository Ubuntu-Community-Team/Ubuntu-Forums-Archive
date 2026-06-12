---
title: "Thunderbird closes for no apperant reason"
date: 2007-01-19
forum: General Help
---

### Post by alibobar on 2007-01-19
Ever since I moved my /home to a new partition (using this guide: 
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)  (some adaptations)). 
I have this problem:

Thunderbird closes for no particular reason when I read an email/rss-feed, after about 5 seconds of viewing the message Tb just disapears, when run from console Tb gives this error: 

$ mozilla-thunderbird
DOUBLE-CLICK: 250 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 12840 Segmentation fault      "$prog" ${1+"$@"}

---

### Post by marianom on 2007-01-22
Segmentation faults errors at startup... If I were you I would report it as a bug in [launchpad]("https://bugs.launchpad.net/thunderbird").

I don't see bugs related to segmentation faults so you might create a new one. If you can generate the crash report file it would be better since you can give devs more info about your problem.

---

### Post by alibobar on 2007-01-23
How can I generate the crash report file?

---

### Post by marianom on 2007-01-23
Type
```
bug-buddy --help
```
in the command line an use one or some of the options you have there (--package, --appname, --pid, etc, etc).

---

