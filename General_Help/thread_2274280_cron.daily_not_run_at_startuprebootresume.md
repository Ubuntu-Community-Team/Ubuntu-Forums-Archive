---
title: "cron.daily not run at startup/reboot/resume"
date: 2015-04-19
forum: General Help
---

### Post by Bjorn_Van_Campenho on 2015-04-19
Hi all,

I have been trying for weeks now to run a simple backup script daily on a laptop. As far as I understood,  it should have been sufficient to just drop the backup script in the /ect/cron.daily directory.  If I run the scrip, it runs fine. If I run all scripts in /etc/cron.daily using run-parts, it also runs fine.

The problem is I can't seem to get anacron to run it after a reboot, even if the data stored in /var/spool/anacron/cron.daily is way back.

in syslog, I get the message:

```
Apr 19 13:53:11 bjvca-XPS-13-9343 systemd[1]: Started Run anacron jobs.
```

but noting seems to happen.  I may need to add I am using Ubuntu 15.04.

---

