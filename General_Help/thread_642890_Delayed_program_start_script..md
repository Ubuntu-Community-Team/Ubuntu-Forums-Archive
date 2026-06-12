---
title: "Delayed program start script."
date: 2007-12-17
forum: General Help
---

### Post by gazmac on 2007-12-17
Hi,

It's a testament to this forum that I have been able to get this far without ever needing to post a question, but now I need a little point in the right direction!

I'm running Ubuntu 7.1 and would like to automatically run the command "wvdial" 5 minutes after start-up and the command "sudo noip2" 7 minutes after start-up. I would like this to be done automatically everytime I reboot the computer.

I would imagine that this requires a script that I run at startup with some delays etc, but I'm completely lost!

Thanks,
Mac

---

### Post by vanadium on 2007-12-17
You can use the "sleep" command to delay a certain time. You can automatically start a script when you log in by adding it to "System - Preferences - Sessions - Startup programs"

You can also autostart "systemwide". To see how that works, you might want to consult a Linux administration guide. Such scripts run as root, so there is no "sudo" needed. The session scripts I outlined before probably run as the current user.

---

