---
title: "any alternatives to logrotate?"
date: 2019-02-04
forum: General Help
---

### Post by Skaperen on 2019-02-04
the default logrotate causes upwards of 10 files per type of log to be changed each day.  this causes my backups to be more demanding than they otherwise would be.  the backups work much like rsync, transferring each file that has changed.  if i wrote my own "logrotate" it would rename each logfile by appending the date.  the ones that are 2 or more days old would be compressed.  the ones that are 10 or more days old would be deleted.  that way there would be fewer changes that are seen to happen and fewer files to be transferred to synchronize the backups.

i just want to check to see if something already exits before i go write my own.

---

### Post by HermanAB on 2019-02-04
Well, just change logrotate.conf to do what you want.  I don't see a need to reinvent the wheel again.

---

### Post by Skaperen on 2019-02-04
> **HermanAB said:**
> Well, just change logrotate.conf to do what you want.  I don't see a need to reinvent the wheel again.

i don't think just changing the config is going to be enough.  some new logic is needed so that when the log file gets a new name that name will stay the same ... except for one more time to compress the file (unless the file gets compressed at the time it first gets its new name) ... no matter how long it will be kept (a week or a few months).

the sliding number thing is what i need to get away from.

---

### Post by Holger_Gehrke on 2019-02-04
Have you taken a look at 'man 5 logrotate.conf' ? If you did, you seem to have missed the options "dateext", "dateformat" and "dateyesterday". As far as I understand it, these seem to do exactly what you want ....

Holger

---

### Post by HermanAB on 2019-02-04
Logrotate can also call a script and in that script, you can do whatever you want.  Some RTFMing is required, but don't write another version of logrotate - there are numerous pitfalls with managing files that are in use that you will learn about the hard way.

---

### Post by Skaperen on 2019-02-05
the way the man page is worded, it would append the date in addition to the sequential number.  does it place the date instead of the sequential number?

---

