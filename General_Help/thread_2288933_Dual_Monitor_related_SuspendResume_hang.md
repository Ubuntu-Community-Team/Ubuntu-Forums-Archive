---
title: "Dual Monitor related Suspend/Resume hang"
date: 2015-07-30
forum: General Help
---

### Post by ButcherBaker on 2015-07-30
Dear Ubuntu fans,
   After upgrading from 13.04 to 14.04 a new problem has arisen.
Suspend/Resume doesn't resume correctly, usually causing a hang.
It only occurs when I have a second monitor connected to the video ports.
The behavior is quite strange; it attempts to resume and the display flashes
on and off several times in different screen resolutions, eventually settling
on the wrong resolution and hanging ... hard reset required.
However, if I tell System Settings to prompt for a password when resuming,
about half the time the flashing will eventually stop and I am able to enter
my password and then the display changes to the correct resolution
and I'm able to proceed normally.  The other half the time it hangs after
trying several different screen resolutions.
  Note I have installed Gnome desktop, but the problem happens regardless
of what Desktop Environment I login to.
  Hardware:  HP 8200 desktop with Intel video:
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09) 
  Any suggestions for fixing this?
Thanks,
BB

---

### Post by ButcherBaker on 2015-08-01
WORKAROUND:  I discovered that release 15.04 doesn't have this problem, so I upgraded and so far the problem has gone away.
BB

---

