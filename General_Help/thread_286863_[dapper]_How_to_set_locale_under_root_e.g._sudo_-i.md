---
title: "[dapper] How to set locale under root? e.g. sudo -i"
date: 2006-10-28
forum: General Help
---

### Post by WillyTP on 2006-10-28
Hi, I've installed Kubuntu Dapper on my server.
I've one problem; while from a user console the locale is properly configured:

> LANG=it_IT.UTF-8
LANGUAGE=it_IT:it:en_GB:en
LC_CTYPE="it_IT.UTF-8"
LC_NUMERIC="it_IT.UTF-8"
LC_TIME="it_IT.UTF-8"
LC_COLLATE="it_IT.UTF-8"
LC_MONETARY="it_IT.UTF-8"
LC_MESSAGES="it_IT.UTF-8"
LC_PAPER="it_IT.UTF-8"
LC_NAME="it_IT.UTF-8"
LC_ADDRESS="it_IT.UTF-8"
LC_TELEPHONE="it_IT.UTF-8"
LC_MEASUREMENT="it_IT.UTF-8"
LC_IDENTIFICATION="it_IT.UTF-8"
LC_ALL=


When I do something as root (e.g., entering a root console with sudo -i) I get the default (wrong) locale:

> LANG=
LC_CTYPE="POSIX"
LC_NUMERIC="POSIX"
LC_TIME="POSIX"
LC_COLLATE="POSIX"
LC_MONETARY="POSIX"
LC_MESSAGES="POSIX"
LC_PAPER="POSIX"
LC_NAME="POSIX"
LC_ADDRESS="POSIX"
LC_TELEPHONE="POSIX"
LC_MEASUREMENT="POSIX"
LC_IDENTIFICATION="POSIX"
LC_ALL=


Anybody knows how to fix that?
Thanks!

---

