---
title: "path name  question"
date: 2006-07-21
forum: General Help
---

### Post by lex1 on 2006-07-21
I got this reply (see this reply below)to a email I sent .

what scrip does the refer to?
suck was insalled with apt-get

suck looks like this:

total 24
drwxrwxr-x 2 news news 4096 2006-06-30 17:16 .
drwxr-xr-x 90 root root 4096 2006-07-21 07:31 ..
-rw-rw-r-- 1 news news 1946 2004-10-27 13:37 get-news.conf
-rw-rw-r-- 1 news news 56 2004-10-27 13:37 suckkillfile
-rw-r--r-- 1 news news 122 2006-07-05 11:15 sucknewsrc
-rw-rw-r-- 1 news news 124 2004-10-27 13:37 sucknewsrc.old





this reply
----------------------------------
> output at end of suck
> /etc/suck/sucknewsrc: Permission denied
> Moving newsrc to backup: Permission denied

chown news [name of your script]

[your script] is the path and name of that script which call suck

chmod 777 etc/suck/sucknewsrc

---

