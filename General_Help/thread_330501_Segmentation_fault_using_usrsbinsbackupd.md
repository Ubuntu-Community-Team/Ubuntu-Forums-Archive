---
title: "Segmentation fault using /usr/sbin/sbackupd?"
date: 2007-01-03
forum: General Help
---

### Post by dannyboy79 on 2007-01-03
Hello, I use simple backup created by gogle summer or code or something like that. Anyway, I believe it installed itself to cron based on the configuration I set it up to use and it has been running great. All of a sudden I get an email from cron the other day telling me that sbackup had a segfault. This was the subject line:
Cron <root@UBUNTU> if [ -x /usr/sbin/sbackupd ]; then /usr/sbin/sbackupd; fi;

and this was in the body of the email:
/bin/sh: line 1:  9175 Segmentation fault      /usr/sbin/sbackupd
 
Is this something I can fix or is this just a once in a while error? As I stated I don't know why this would happen as the location the backup gets written to has proper permissions and has plenty of space. Any help would be appreciated.

---

