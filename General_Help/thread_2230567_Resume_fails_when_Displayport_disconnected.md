---
title: "Resume fails when Displayport disconnected"
date: 2014-06-19
forum: General Help
---

### Post by ingenium2 on 2014-06-19
If I suspend my laptop with a monitor connected via DisplayPort, and the screen is off (set to turn off after 10 minutes of inactivity), resuming will fail if and only if the monitor has been disconnected. 

Steps to reproduce:

[LIST]
[*]Connect a monitor with DisplayPort
[*]Let the computer idle and wait for the display to turn off
[*]Suspend the system (ie close the lid)
[*]Unplug the DisplayPort monitor
[*]Try to resume
[/LIST]
The system itself turns on, but the laptop display never turns on and it never finishes waking up (wifi indicator light for example doesn't turn on). Ctrl+Alt+F1, etc does not work. Closing the lid will not trigger it to suspend again. It's basically completely locked up. The system does respond to SysRq though (the usual REISUB will trigger a reboot). 

However, if I move the mouse and wake the screen up before suspending, then it resumes fine. If the screen is off when it's suspended, but the DisplayPort monitor is not unplugged, then resuming will work. It's only when both the screen is off and the DisplayPort monitor is disconnected that resume fails. 

I looked through syslog, kern.log, and pm-suspend.log, but there are only lines for the suspend and subsequent boot. There's nothing even showing it tried to resume. 

I have a Thinkpad T430, running Ubuntu 14.04.

---

