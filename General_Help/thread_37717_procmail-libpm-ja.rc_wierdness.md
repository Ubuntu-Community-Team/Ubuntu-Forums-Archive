---
title: "procmail-lib/pm-ja*.rc wierdness"
date: 2005-05-28
forum: General Help
---

### Post by jontibs on 2005-05-28
I'm having problems with the pm-ja* procmail modules, distributed as part of procmail-lib in universe. If I pipe a message through the following procmailrc:

SHELL=/bin/sh
MAILDIR=${HOME}/tmp/Mail_test
DEFAULT=${MAILDIR}/default
PMSRC=/usr/share/procmail-lib
INCLUDERC=${PMSRC}/pm-javar.rc

:0
| gzip >>output.gz

I get the following error:

gzip: gzip: No such file or directory
procmail: Error while writing to " gzip >>output.gz"

If I comment out the INCLUDERC line, it works as expected. I get the same problem with all and only the modules that (transitively) INCLUDERC pm-javar.rc. Any ideas what the problem is? I'm new to procmail, so please tell me if I'm doing something I shouldn't.

---

