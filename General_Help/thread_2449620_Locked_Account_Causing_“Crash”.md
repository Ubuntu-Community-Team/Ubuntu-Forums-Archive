---
title: "Locked Account Causing “Crash”"
date: 2020-08-30
forum: General Help
---

### Post by temp1029 on 2020-08-30
Intermittently on my 20.04 install when the screen is locked (either manually or automatically) I am unable to get the login screen to come up. I have three monitors and only one appears to be on, the other two hibernating. Moving the mouse or hitting keys doing nothing, the only way to "solve" it is a hard power-off and restart.

I've gone through my usual research of looking at the syslog and checking for files /var/crash but nothing jumped out at me. The closest I got was possible a problem with gnome-shell, but couldn't ever verify the issue. Automatic suspend is disabled, so I don't think it is a hibernation issue.

This is a mostly clean install, which I primarily use for programming. I have added things like PHP, docker, mysql, npm, etc but none of those need to be running for this issue to occur. I have tried to reproduce it but have been unable.

I was hoping for suggestions on next steps, possible causes, pretty much anything since I'm at the limit of what I know how to do.

**Hardware**
[LIST]
[*]CPU: Intel(R) Core(TM) i7-9700KF CPU @ 3.60GHz 8-Core
[*]Memory: 32GB DDR4 2666 Mhz
[*]Graphics: Radeon PRO WX 3200
[/LIST]

---

