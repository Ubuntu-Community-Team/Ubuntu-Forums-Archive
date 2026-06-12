---
title: "restart messages in the syslog"
date: 2007-05-22
forum: General Help
---

### Post by smsmith050 on 2007-05-22
May 21 07:35:09 xxxxxx-ubuntu704 syslogd 1.4.1#20ubuntu4: restart.

I see a restart message in my syslog however I did not restart the system at 07:35:09. There are not the usual kernel messages after the restart message. 

Is this an error in the logging software?

regards:confused:

---

### Post by mitch.c on 2007-05-22
> **smsmith050 said:**
> May 21 07:35:09 xxxxxx-ubuntu704 syslogd 1.4.1#20ubuntu4: restart.

I see a restart message in my syslog however I did not restart the system at 07:35:09. There are not the usual kernel messages after the restart message. 

Is this an error in the logging software?

Don't worry. The syslog daemon is restarting, not your system. This typically happens after a log rotation.

Cheers
-- 
Mitch

---

