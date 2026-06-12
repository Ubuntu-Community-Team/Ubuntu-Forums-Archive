---
title: "Mails from Anacron about openoffice.org 2"
date: 2005-04-05
forum: General Help
---

### Post by herweg on 2005-04-05
Ever since I installed the openoffice.org 2 packages, I get daily emails from cron.daily, and weekly emails from cron.weekly that state
```
/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/ooffice2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oohtml2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooweb2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oocalc2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oofromtemplate2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oowriter2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooimpress2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oodraw2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oomath2.1.gz is a dangling symlink

```
Any ideas as to why this is happening and what I can do to fix it?

---

### Post by sas on 2005-04-05
[QUOTE=herweg]Ever since I installed the openoffice.org 2 packages, I get daily emails from cron.daily, and weekly emails from cron.weekly that state
```
/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/ooffice2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oohtml2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooweb2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oocalc2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oofromtemplate2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oowriter2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooimpress2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oodraw2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oomath2.1.gz is a dangling symlink

```
Any ideas as to why this is happening and what I can do to fix it?[/QUOTE]

The file that /usr/share/man/man1/oomath2.1.gz (for example) is pointing to no longer exists, i'm not sure why, something to do with the OO package I guess.

---

