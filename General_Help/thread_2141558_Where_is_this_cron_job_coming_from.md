---
title: "Where is this cron job coming from?"
date: 2013-05-03
forum: General Help
---

### Post by pmains on 2013-05-03
Running Ubuntu 12.10 desktop, but with a number of server daemons installed and running:

Every hour, at minute 17, I'm seeing this message in auth.log:

*May  1 18:17:01 derp CRON[7205]: pam_unix(cron:session): session closed for user root*

When I change my session to the root user, and type *crontab -l*, the output is *no crontab for root*. I'm guessing that this is something pretty normal and benign, but I wanted to make sure. Is there another location that I should be looking for to see where this mysterious cron behavior is coming from? Is this not cron behavior at all? Is it possible that, say, my SQL server, Apache server, etc. are causing this behavior?

---

### Post by Old_Grey_Wolf on 2013-05-03
This is normal.

cron has to be authenticated with the pam system just like everyone else. cron checks config files to see if anything has changed periodically. That is want you are seeing, the pam_unix sessions opening and closing. On some Linux systems it happens every 10 minutes.

---

