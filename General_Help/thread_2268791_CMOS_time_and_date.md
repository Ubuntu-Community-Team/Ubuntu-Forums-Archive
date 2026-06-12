---
title: "CMOS time and date"
date: 2015-03-11
forum: General Help
---

### Post by michael-piziak on 2015-03-11
I know my Ubuntu gets it's time and date from an online server.  Does it also set the bios time and date ?

---

### Post by tgalati4 on 2015-03-12
Yes, but the battery on the motherboard needs to be functional to keep the correct time.  A computer that doesn't keep time after reboot generally means that  the motherboard battery is dead.

Also BIOS time is typically UTC and Linux applies a correction using the local timezone.  BIOS real time clock (RTC) typically gets set at shutdown so that when you resume from sleep or reboot the RTC then dumps its time into the kernel software clock.  The RTC may be syncronized more often using system commands.

---

