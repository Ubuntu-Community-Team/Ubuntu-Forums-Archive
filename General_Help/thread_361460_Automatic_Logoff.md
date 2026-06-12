---
title: "Automatic Logoff"
date: 2007-02-14
forum: General Help
---

### Post by neubs007 on 2007-02-14
I just installed xubuntu 6.10 on my old k6-3 450.  After I successfully log in, it logs me off within a couple of seconds.  Sometimes if I start an application like firefox it will let me work with the application until I close it; then it kicks me out again.  This happens in both the live cd and once installed on the hdd.  It doesn't happen with 6.06 but I have other issues with that version.  If I could get it to work with 6.10 that would be ideal.

Any ideas on how to stop it from continuously logging me off?

---

### Post by mssever on 2007-02-14
Sounds like something is dying that shouldn't. Is there anything relevant in the logs?
[LIST]
[*]~/.xsession-errors
[*]/var/log/*[/LIST]

---

