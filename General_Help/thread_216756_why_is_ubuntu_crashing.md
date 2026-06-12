---
title: "why is ubuntu crashing?"
date: 2006-07-16
forum: General Help
---

### Post by Trab on 2006-07-16
ubuntu has been crashing recently more than usual, its very frustrating.
totally frozen machine.
i cannot drop X, i cannt check task manager, everything freezes.
when i reboot, how can i determine what is causing the problem (so i can work towards resolving it)
thanks much,
Trab

---

### Post by hanzomon4 on 2006-07-16
Check the system monitor to see if any apps are sucking a large amount of ram

---

### Post by Trab on 2006-07-16
im looking more as logs of what might have happend?
cheers,
Trab

---

### Post by kripkenstein on 2006-07-16
Well, /var/log contains the log files. You can check the latest-updated ones to see if there is anything.

However, there are other things you can check about such random instability. As hanzomon4 said, make sure memory usage is within reasonable limits. Another thing to check is system temperature. You can also test your system RAM with memtest, this might be a hardware issue (it could also be hardware other than the RAM).

Also try to see if the problems occur at particular times (when a particular program is running, for example).

---

