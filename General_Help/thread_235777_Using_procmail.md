---
title: "Using procmail"
date: 2006-08-13
forum: General Help
---

### Post by pat270881 on 2006-08-13
Hi,

I want to use procmail - so I installed the package procmail using synaptic.

Then I created a .procmailrc-file under /var/spool/mail:

```

# .procmailrc
PATH=/usr/bin:/usr/local/bin
MAILDIR=/var/spool/mail
LOGFILE=/dev/null
SHELL=/bin/bash

:0:
* ^(From|Cc|To).*VIAGRA.*
spam

```

Furthermore I created a spam directory under /var/spool/mail - so that the procmail rule works and mails with VIAGRA in sender will be removed in the spam directory. Unfortunately, this does not work...

Does anybody know here what went wrong?:confused:

---

### Post by llamakc on 2006-08-13
.procmailrc goes in your /home directory. Move it there.

---

