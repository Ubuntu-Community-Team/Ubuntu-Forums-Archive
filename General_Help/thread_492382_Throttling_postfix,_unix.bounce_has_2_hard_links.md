---
title: "Throttling postfix, unix.bounce has 2 hard links"
date: 2007-07-04
forum: General Help
---

### Post by PgR on 2007-07-04
Hi folks,

When I send email via my (local) postfix installation and it isn't passed on (their MX doesn't respond, or they reject it, or whatever)  I get hundreds of messages like this in syslog

> Jul  4 21:49:12 spitfire postfix/bounce[16057]: fatal: open lock file pid/unix.bounce: file has 2 hard links
Jul  4 21:49:13 spitfire postfix/master[15937]: warning: process /usr/lib/postfix/bounce pid 16057 exit status 1
Jul  4 21:49:13 spitfire postfix/master[15937]: warning: /usr/lib/postfix/bounce: bad command startup -- throttling

with incrementing process numbers.

The only solution I've found is to track the email down in /var/spool/postfix/active and delete it.

How can I stop this happening?

PgR

---

