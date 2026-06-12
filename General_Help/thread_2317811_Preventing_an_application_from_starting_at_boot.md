---
title: "Preventing an application from starting at boot"
date: 2016-03-20
forum: General Help
---

### Post by AussieGuy on 2016-03-20
This should be a trivial matter, but it's got me beat.  Some time ago my system (running on a laptop) powered off when the battery power ran out.  And since then, whenever I've needed to reboot, I've had shotwell starting up - this must have been a program running when the system first stopped.

I don't want it; it's annoying.  The trouble is, I can't find for the life of me where the configuration or settings file is which tells my system to start shotwell.  I'm running KDE, but it's not listed in the KDE autostart directory.  Nor is it in /etc/rc.local, /etc/xdg/autostart, or any of the files related to my shell, zsh.  I've performed innumerable "grep -R shotwell ." on different directories, and found nothing.  My Session Management has "Restore previous session" ticked, but even if I kill shotwell, if keeps bouncing back on a reboot.

Something, somewhere must be starting shotwell automatically... but where?  And what?  And how do I find it?

Thanks,
-A.

---

### Post by matt_symes on 2016-03-20
Hi

I would start by deleting the old session data folder(s), even though you close it and it's still reappearing after reboot, just in case the old session data was corrupted by the power failure.

Kind regards

---

### Post by Bucky Ball on 2016-03-20
When at the desktop, make sure all apps are closed, go for a restart and in that GUI with 'restart, logout, shutdown, etc.' you will see a tick box 'save session for next time' or something like that. Tick it and restart. 

Next time you shut down, make sure that box is unticked. Failing that, matt_symes is probably heading in the right direction. :)

---

### Post by vasa1 on 2016-03-20
> **AussieGuy said:**
> ...  I'm running KDE ...
Is this Kubuntu? Or is it something + KDE and which version of KDE? I notice you have zsh?

---

