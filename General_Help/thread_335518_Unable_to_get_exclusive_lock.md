---
title: "Unable to get exclusive lock"
date: 2007-01-10
forum: General Help
---

### Post by xGutsAndGloryx on 2007-01-10
This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.


what does this mean? why is it giving me that error message when i have no other application running. i could have everything closed and try to update only to get that error message.



please help me out!

---

### Post by Johnsie on 2007-01-10
This happen sometimes if you have problem with your package manager.

Try saving your work and pressing alt-ctl-backspace. That wil restart gnome without you needing to reboot

If that doesn't work try rebooting.

---

### Post by paparucino on 2007-01-10
> **xGutsAndGloryx said:**
> This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

what does this mean? why is it giving me that error message when i have no other application running. i could have everything closed and try to update only to get that error message.
!
Try:
```

System -> Administration -> System monitor -> Processes

```
Check the list of the processes to see if there is an instance of some apt-get, aptitude, update-manger, then kill it. (right-click on the process then "kill process").
Sometimes this situation happens to me with firefox.

---

### Post by Johnsie on 2007-01-10
That is probably the better solution... only try mine if that fails.

---

