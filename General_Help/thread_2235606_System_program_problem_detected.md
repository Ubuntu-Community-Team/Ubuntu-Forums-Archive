---
title: "System program problem detected"
date: 2014-07-22
forum: General Help
---

### Post by Lappert on 2014-07-22
Running Ubuntu server 14.04 with Kubuntu desktop.

When I boot up I get a pop-up notice that reads "System program problem detected" and "Do you want to report the problem now?"

Clicking Report Problem, I get a second note that says, "Sorry, Ubuntu 14.04 has experienced an internal error. If you notice further problems, try restarting the computer." It then allows me to send an error report.

Clicking "Show Details" I get a screen that says "Executable Path" and "/usr/bin/Xorg" and then the small animated circle, but that takes a number of minutes to complete. 

Finally, I get a VERY long detail:

> xserver-xorg-core 2:1.15.1-0ubuntu2
Crash
Xorg crashed with SIGABRT in OsAbort()
.proc.driver.nvidia.gpus.0
...


It's a long notice and copy/paste isn't working on it. I'm guessing there might be 30 more lines. If I can find where the notice might be, I'll try to post the complete details on a follow-up post.

This  has been appearing every time I boot up. 

Any thoughts? Thank you.

---

### Post by Bashing-om on 2014-07-22
Lappert; Hello;

1st is to see if the package manager is happy:
Issue terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
Post back any error that the system may generate.

Then is to look at the log files.
```

less /var/log/Xorg.0.log
less ~/.xsession-errors

```

Maybe then there is enough info to look at what that "internal error" is all about.

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by Lappert on 2014-07-23
Thanks for your reply.

No errors on apt-get... (I run those almost daily).

Seems Xorg.0.log is around 32K. You don't want me to paste the entire thing, I assume. Let me know if you want an uploaded attachment of the file.

OTOH, .there are two .xsession-errors files:

> Script for none started at run_im.Script for auto started at run_im.
Script for default started at run_im.
init: upstart-dbus-session-bridge main process (2689) terminated with status 1
init: Disconnected from notified D-Bus bus
init: startkde main process (2773) killed by TERM signal
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 98545 requests (98545 known processed) with 2 events remaining.


and

> Script for none started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: upstart-event-bridge main process (2957) terminated with status 1
init: upstart-event-bridge main process ended, respawning
init: upstart-dbus-system-bridge main process (2977) terminated with status 1
init: upstart-dbus-system-bridge main process ended, respawning
init: upstart-dbus-session-bridge main process (2979) terminated with status 1
init: upstart-dbus-session-bridge main process ended, respawning
init: upstart-file-bridge main process (2983) terminated with status 1
init: upstart-file-bridge main process ended, respawning


---

