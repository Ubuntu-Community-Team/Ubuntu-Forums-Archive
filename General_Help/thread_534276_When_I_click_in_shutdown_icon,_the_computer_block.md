---
title: "When I click in shutdown icon, the computer block"
date: 2007-08-25
forum: General Help
---

### Post by hraposo on 2007-08-25
I'v a problem:
When I click in shutdown icon, the computer blocks.
Wha is the command of sutdown icon?
How can I solve this problem?

---

### Post by r4ik on 2007-08-25
As root in a terminal,

 shutdown now

Good luck !

---

### Post by apetresc on 2007-08-25
> **hraposo said:**
> I'v a problem:
When I click in shutdown icon, the computer blocks.
Wha is the command of sutdown icon?
How can I solve this problem?

What usually causes this problem is a poorly configured cpufreqd. Have you:
a) Manually recompiled your kernel? (And not enabled CPU Frequency Scaling while doing so)
b) Modified your init runlevels? (Specifically, removed cpufreqd)
c) Removed the cpufreqd/powernowd packages?

Any of those may have caused this. ```
sudo shutdown -h now
``` should still work though.

---

### Post by hraposo on 2007-08-25
I don't do nothing of it. This appen with no apparent reason... But the button thats control the restart, shutdown, logoff, had a command... Whitch command?

---

### Post by apetresc on 2007-08-25
> **hraposo said:**
> I don't do nothing of it. This appen with no apparent reason... But the button thats control the restart, shutdown, logoff, had a command... Whitch command?
Essentially the command I gave above, ```
sudo shutdown -h now
```

---

### Post by capink on 2007-08-25
Which desktop environment are you using? do you log in using gdm or startx? if it is the later you may want to add /sbin/shutdown to sudoers file.

---

