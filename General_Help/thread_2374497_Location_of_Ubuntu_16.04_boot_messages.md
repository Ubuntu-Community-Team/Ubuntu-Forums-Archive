---
title: "Location of Ubuntu 16.04 boot messages?"
date: 2017-10-16
forum: General Help
---

### Post by walker452 on 2017-10-16
Where can one find the boot messages of Ubuntu 16.04?

I've looked in /var/log but see no boot msg log file.

Thanks,

---

### Post by ian-weisser on 2017-10-16
They are usually appended to /var/log/syslog.
Note that syslog rotates daily, so if syslog doesn't go back far enough then look in /var/log/syslog.1

---

### Post by walker452 on 2017-10-17
> **ian-weisser said:**
> They are usually appended to /var/log/syslog.
Note that syslog rotates daily, so if syslog doesn't go back far enough then look in /var/log/syslog.1

Got it... Thanks.

---

