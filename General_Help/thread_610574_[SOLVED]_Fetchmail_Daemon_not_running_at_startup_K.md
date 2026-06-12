---
title: "[SOLVED] Fetchmail Daemon not running at startup Kubuntu"
date: 2007-11-12
forum: General Help
---

### Post by keyboardashtray on 2007-11-12
I've setup fetchmail to run, then I used the command -fetchmail -d 600 to run the daemon. 

It is my understanding that the general method of configuring session programs is simply to have a given program running when you logout.

Well, I've done that, and when I check in Runlevel Editor (system services) fetchmail is there, it is marked start at boot, but it is not running.

When I run Ksysguard, however, the daemon is not in the processes. I have to retype the daemon command.

Am I missing something?

Edit: I also want to mention that if I only log out, without rebooting, it remains in the processes list. But if I reboot, this is when it isn't running.

---

### Post by keyboardashtray on 2007-11-12
Well, it didn't seem like the way I should have to do it, but I downloaded a control center module Autostart (why doesn't this come with Kubuntu?) and was able to add it to an autostart list. The autostart module then crashed :( but the daemon starts now.

---

