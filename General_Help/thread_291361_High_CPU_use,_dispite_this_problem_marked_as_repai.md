---
title: "High CPU use, dispite this problem marked as repaired @ launchpad?"
date: 2006-11-02
forum: General Help
---

### Post by hardyn on 2006-11-02
I have done a fair bit of reading about this excessive CPU usage. and it appears as if has been fixed (launchpad) but i still have to use the max_cstate switch to get my machine to idle properly.

[https://launchpad.net/distros/ubuntu...eta/+bug/30570](https://launchpad.net/distros/ubuntu...eta/+bug/30570)

adding this line to startup script:
"echo 1 > /sys/module/processor/parameters/max_cstate"
does take care of the problem, but i understood that this was a quick fix and not real a solution.  as the case has been marked as closed and repaired why is this still broken for me?  I understand that this problem is isolated to P-M based machines, which there must be millions, so i cant be the only one with this problem even under edgy.

thanks for any help.

edgy 6.10
asus z70va 1024mb x700 w/ radeon drivers
pentium m CPU

---

### Post by pasipasi on 2006-12-14
I have the same issue with the generic kernel and that command seems to fix it - my fan shuts down and the cpu speed drops down to half. My processor is Pentium M 740.

Linux samperi 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

---

### Post by Castar on 2007-02-11
Which script is this?

---

### Post by hardyn on 2007-02-11
i dont recall, but im sure a few seconds of poking around will reveal it.

the new solution is to use the 386 kernel, which is now a generic uniprocessor kernel.

---

