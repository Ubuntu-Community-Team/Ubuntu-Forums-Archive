---
title: "Ubuntu intermittently cannot shut down because of a stop job"
date: 2018-10-21
forum: General Help
---

### Post by buisteric on 2018-10-21
Hi,
I am getting this problem from time to time, not always. When I shutdown or restart, the system hangs, waiting for a stop job. There is no indication of the name of that stop job, and it will never stop until a 1m30s timeout elapses. Sometimes, another stop job blocks like this, so it can take minutes to shutdown or reboot. Since my upgrade to 18.10, it does that EVERY restart, and the last time, it wasn't finishing so I had to power off my computer forcibly to get out of this.
First, what is a "stop job" exactly? Then what log files could help figure out what is going on? Maybe additional logging needs to be turned on to see what is hanging?
Thanks for any help.

---

### Post by Dennis N on 2018-10-21
I also have been seeing this as an intermittent problem. Some process is failing to terminate as it should.

Bug report filed (way back in 2015; considered "low importance" and never was assigned to be solved):
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

Comments from the bug report help explain the shutdown process:

Expert Martin Pitt quoted from comment section of bug report:
> 
"What happens at shutdown is that all processes are sent SIGTERM, so that they have a chance to intercept, save their state/clean up, etc. After a timeout (default 90s) SIGKILL is sent."

"This [problem] probably got introduced with the fix for bug 1448259. So, this general behaviour is "correct" in the sense that processes should not be killed immediately after SIGTERMing them. But 90s is a bit much for session shutdowns, this could be reduced to something like 30 s. This is still a long session shutdown, but you really wan this if e. g. LibreOffice asks you about unsaved documents and the like.

I don't know what the timeout under upstart was, but apparently it was a lot smaller."

Posted on alt.os.linux google group:
> 90-second startup and shutdown delays: systemd?

It is a systemd issue. I experienced it on shutdown on Debian Sid.
I ended up setting some systemd timeout down to 5 seconds.

[https://bugs.launchpad.net/ubuntu/+s...d/+bug/1457400](https://bugs.launchpad.net/ubuntu/+s...d/+bug/1457400)

/etc/systemd/system.conf

or a similar file should be your friend

[http://www.freedesktop.org/software/...stem.conf.html](http://www.freedesktop.org/software/...stem.conf.html)

search for

DefaultTimeoutStartSec=
DefaultTimeoutStopSec=
TimeoutSec=

and enter lower values

Good luck!
...


Comment: Long ago, I tried the suggestion above, but lower times just seemed to be ignored. The problem doesn't happen very often on my system (I believe its been only on Gnome or MATE for me), so if it does, I just wait it out.

---

