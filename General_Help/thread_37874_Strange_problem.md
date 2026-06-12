---
title: "Strange problem"
date: 2005-05-29
forum: General Help
---

### Post by NeoChaosX on 2005-05-29
Okay, I'm having this weird occurance with Ubuntu, and i don't know what's going on. When I check the Unix mail (with the 'mail') command, I almost daily have a mail about a problem with  the same cronjob, man-db. When I do open the mail, I get this output:

```
/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/oowriter2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooimpress2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooweb2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oocalc2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oohtml2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oomath2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oodraw2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oofromtemplate2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooffice2.1.gz is a dangling symlink

```
Now what it is trying to tell me? It has to do something with the man pages for OpenOffice2, but I don't know what man-db does, or why it's having problems with those files. Can anybody enlighten me to what's going on?  :-?

---

### Post by jasmuz on 2005-05-29
[QUOTE=NeoChaosX]Okay, I'm having this weird occurance with Ubuntu, and i don't know what's going on. When I check the Unix mail (with the 'mail') command, I almost daily have a mail about a problem with  the same cronjob, man-db. When I do open the mail, I get this output:

```
/etc/cron.daily/man-db:
mandb: warning: /usr/share/man/man1/oowriter2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooimpress2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooweb2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oocalc2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oohtml2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oomath2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oodraw2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/oofromtemplate2.1.gz is a dangling symlink
mandb: warning: /usr/share/man/man1/ooffice2.1.gz is a dangling symlink

```
Now what it is trying to tell me? It has to do something with the man pages for OpenOffice2, but I don't know what man-db does, or why it's having problems with those files. Can anybody enlighten me to what's going on?  :-?[/QUOTE]
 When you get a report it means something has gone in a whay you dont expect it.
Cron is a scheduler program...and man-db, keeps track of the man pages in your system..
Its telling you that those pages have symlinks,...yet they dont exist.

I can only recomend you to look at those links and eliminate them by yourself.

---

### Post by NeoChaosX on 2005-05-29
Just did that. Can't believe I didn't think of that before. Thanks.

---

