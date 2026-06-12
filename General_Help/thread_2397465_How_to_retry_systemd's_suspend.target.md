---
title: "How to retry systemd's suspend.target?"
date: 2018-07-29
forum: General Help
---

### Post by goatboy73 on 2018-07-29
Hi!

In my system, suspend/resume works fine. However, I use a backup tool that I run hourly, and I don't want the system to suspend while that tool is running (backups are more important than the extra juice I'd save by suspending early).  I've achieved that, but now I've run into an interesting conundrum.

When the system tries to suspend due to idle timeout (I've been AFK for 15+ minutes, for instance), but the backup tool is running at that moment, then the suspend will be inhibited (correctly!), but then later on the system will not retry the suspend.  That is to say: systemd assumes the suspend failure is a hard fail, and thus shouldn't be retried.

I want to modify this behavior so that systemd can either be told to suspend again, or to retry a suspend-by-timeout after 60 seconds (?) if it fails to execute the first time.

I'd very much like to avoid coding this retry into my scripts, since the whole idea is to achieve this via the system's and OS's inherent infrastructure.  I know I can use systemd-inhibit to achieve temporary blocks (i.e. block while X program is running), but I'm not entirely positive it works as I expect it to since I can successfully suspend the system even when a sleep block is in place.

The way I have it structured is via this unit:

```
[Unit]
Description=Inhibit suspend in case of backup activity
Before=sleep.target


[Service]
Type=oneshot
ExecStart=/bin/bash -c "/usr/bin/check-backup-is-inactive"


[Install]
RequiredBy=sleep.target

```

The problem that systemd reports in the logs is that a dependency (i.e. ***RequiredBy***) for sleep.target has failed, and thus sleep.target is not achieved.  This is perfect.  The problem is that no future attempt is made to sleep again, so when the backup is done and it's OK to suspend, there is no attempt made.

The trickiest part is this: what happens if a "retry" is schedules, but I've returned to the keyboard and a "queued" suspend (through a retry) is no longer appropriate?  This is why I don't want to code it explicitly - things start to get really gnarly, really quickly ;)


So...Thoughts?

---

