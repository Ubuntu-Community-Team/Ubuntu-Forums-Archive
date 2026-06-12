---
title: "ssmtp authentication doesn't work for cron"
date: 2007-09-23
forum: General Help
---

### Post by jelevin on 2007-09-23
I'm trying to switch internet providers and the new one requires that outgoing mail be authenticated.  I have modified the ssmtp.conf file to add the userid and password and this works when I send mail from the command line.  Unfortunately, the cron emails fail with this error message in the mail error log file "Sep 23 00:41:33 mango sSMTP[14358]: Authorization failed (535 Authentication failure)"

Any thoughts?

---

