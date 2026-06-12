---
title: "no automatic suspend"
date: 2018-08-14
forum: General Help
---

### Post by ulrichmuc on 2018-08-14
I am running Ubuntu Mate 16.4 LTS on an Eee PC netbook.  
Kernel: 4.4.0-131-generic

Via power management preferences I requested sleep after 30 minutes of idling.
This works a few times after booting. 
However, after a while, it ceases to work: I get the screensaver picture, but no suspend.
After rebooting, it works again - a few times.
I suspect that there is some process active which prevents automatic suspend, but do not know how find it.
Of course, I can suspend by hand.

Any ideas?

---

### Post by TheFu on 2018-08-15
I've never used a GUI to manage power settings.

There are settings in /etc/systemd/logind.conf which control what happens when the system is idle for a period of time.  From the manpage for logind.conf:
```

       IdleAction=
           Configures the action to take when the system is idle. Takes one of
           "ignore", "poweroff", "reboot", "halt", "kexec", "suspend",
           "hibernate", "hybrid-sleep", and "lock". Defaults to "ignore".

           Note that this requires that user sessions correctly report the
           idle status to the system. The system will execute the action after
           all sessions report that they are idle, no idle inhibitor lock is
           active, and subsequently, the time configured with IdleActionSec=
           (see below) has expired.

       IdleActionSec=
           Configures the delay after which the action configured in
           IdleAction= (see above) is taken after the system is idle.
```
After changing, I think the system needs to be rebooted for the changes to become effective. Might work just to restart systemd-logind.service.  I don't know if 18.04 properly reports the system as idle either.

---

### Post by ulrichmuc on 2018-08-20
The question was not, how to request suspend after some idle time. It works fine via GUI.
The question is, why - after some successful suspends - the system does not anymore recognize idling.

---

