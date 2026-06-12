---
title: "Strange screen issue."
date: 2014-10-04
forum: General Help
---

### Post by Marinus_Leeuwerik on 2014-10-04
Hello,

Yesterday I installed the latest LTS build of Ubuntu (14.04.1) on my brother's PC.
Everything was fine and well, I correctly installed the latest display drivers for his graphics card (AMD Radeon HD6450). But now, his pc has a weird screen issue. It blackens out, and few seconds later it turns back on (like it is going in power saving mode). This happens quite often, it's fairly annyoing for him to work with, I tried to reinstall the graphics drivers, but no success so far. If any one knows or could help me to solve this issue, would be greatly appriciated!

Regards, Marinus Leeuwerik

---

### Post by Rob Sayer on 2014-10-05
You may have correctly installed the incorrect drivers.  You're clearly getting an incorrect result.  Which video driver is in use?

According to this:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

the open source radeon driver for the 6450 should work fine.

I never install proprietary drivers anymore unless there's a problem with the open source one, and then I look it up first.  Some of those factory supported adapters aren't actually supported properly.

---

### Post by buzzingrobot on 2014-10-05
I've also found the proprietary AMD drivers to be flaky.

If you installed the proprietary driver via Additional Drivers, use it again to remove it and revert to the open source driver that's installed and used by Ubuntu by default. You need to reboot before new drivers take effect.

---

### Post by Bucky Ball on 2014-10-05
Sounds dumb, but the screensaver or power management aren't set to switch the screen off if no activity for 'x' seconds by default, in this case, probably 2 minutes or something???

---

### Post by Dennis N on 2014-10-05
First thing I would check with those symptoms is the video cable to the monitor - could be loose at either end causing intermittent loss of signal. Happened to me once and took a while to realize what was going on.

---

