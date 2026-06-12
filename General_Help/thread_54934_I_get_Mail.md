---
title: "I get Mail"
date: 2005-08-06
forum: General Help
---

### Post by wjp.reg on 2005-08-06
```
From [email]root@localhost.loca[/email]ldomain  Tue Aug  2 07:35:54 2005
X-Original-To: root
From: Anacron <root@localhost.localdomain>
To: [email]root@localhost.loca[/email]ldomain
Subject: Anacron job 'cron.daily' on gubuntu
Date: Tue,  2 Aug 2005 07:35:54 -0400 (EDT)

/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/x-www-browser.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/mozilla.1.gz is a dangling symlink

```

I get the above mail message it seems on every boot.  Can someone tell me what it means?

I see it consistently repeated in my system mail.

Thanks!

---

### Post by dave9191 on 2005-08-06
It means that those symlinks (shortcuts in windows lingo) point to non existing files. You can either find out what happened to the files or delete those symlinks. 

Dave

---

### Post by jasmuz on 2005-08-06
It means that those links arent working anymore because of system modifications, to stop getting them just do the following:

sudo rm /usr/share/man/man1/x-www-browser.1.gz
sudo rm /usr/share/man/man1/mozilla.1.gz

---

### Post by wjp.reg on 2005-08-06
Thanks!

---

