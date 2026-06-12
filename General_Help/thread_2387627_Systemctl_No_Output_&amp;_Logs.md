---
title: "Systemctl No Output &amp; Logs"
date: 2018-03-21
forum: General Help
---

### Post by omfgod on 2018-03-21
Hi

Not sure what I might have done to affect this but I no longer get any output from systemctl commands, ie status, --help, man systemctl, basically everything.

I also at the around the same time stopped getting logs to my syslog and messages files - presuming it may be linked? I use syslog-ng but everything else is running fine.

Anyone got any idea? normally google is able to fix anything I have an issue with but this has stumped us!

Thank you for your help.

---

### Post by mc4man on 2018-03-21
Is rsyslog installed?

---

### Post by omfgod on 2018-03-21
> **mc4man said:**
> Is rsyslog installed?

No

---

### Post by omfgod on 2018-04-14
Below fixed it.

export SYSTEMD_PAGER=$LESS

---

### Post by wildmanne39 on 2018-04-14
Please use thread tools at the top of the page to mark the thread solved!

Thanks

---

