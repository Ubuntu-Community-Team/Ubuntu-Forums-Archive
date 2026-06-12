---
title: "Cron job to remote machine when sleep mode."
date: 2013-09-03
forum: General Help
---

### Post by charles6 on 2013-09-03
Hi guys,

I have a question regarding cron jobs.  I want to setup some jobs using rsync to a remote machine, these jobs will most likely run overnight.  If my remote machine is in sleep mode at the time my unbuntu server is attempting to execute the rsync job at the time, what will happen to the job?  Will it execute once the machine comes back up or will it just simply fails and attempt to execute on the next scheduled time?


Thanks.

---

### Post by scbingham on 2013-09-03
I'd say the job will just fail until the remote machine is awake the next time the job is scheduled.

This might help you out: [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

I've never tried it, be interesting if it works for you.

---

### Post by ian-weisser on 2013-09-03
> **charles6 said:**
>  If my remote machine is in sleep mode at the time my unbuntu server is attempting to execute the rsync job at the time, what will happen to the job?  Will it execute once the machine comes back up or will it just simply fails and attempt to execute on the next scheduled time?

The job will simply fail, and attempt to execute at the next scheduled time.

scbingham is right: Use a magic packet to wake the remote machine, wait a few seconds for the remote machine to come up, do a test connection to ensure the remote machine is ready, then do the rsync.

Some older hardware does not support Wake On Lan (WOL), and WOL is designed to work on a LAN (not the internet or across a router). There are workarounds to the latter.

---

### Post by charles6 on 2013-09-04
Thanks guys, i'll have a look.  I figured that it wouldn't execute when coming back up.

---

### Post by Lars Noodén on 2013-09-04
If you need a one-off action, then you could run [at](http://manpages.ubuntu.com/manpages/raring/en/man1/at.1.html) which should execute next time the machine is up.  If you want cron-like job control but on a machine that may not be active all the time,  then you may want [anacron](http://manpages.ubuntu.com/manpages/precise/man8/anacron.8.html), but it is limited to jobs run once a day or less frequently.

---

