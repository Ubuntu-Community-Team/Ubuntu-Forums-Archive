---
title: "A Real Stumper..."
date: 2007-05-19
forum: General Help
---

### Post by ephman on 2007-05-19
hi,

here's the scoop.  i'm running fiesty on my intel 1.7 ghz.  i'm running a few boinc 5.4.11, projects (rosetta, climate) which maxs out the cpu.  now without any changes to the system i've noticed that my cpu won't go over 600Mhz running boinc.  just happened the other day.  it's like the intel sidesteps the chip down.  wierd.  however when i'm running any other programs and the cpu needs everything its got the chip works just fine and will go up to the 1.7 ghz.  but when that process is over it'll go back down to the 600 mhz while running boinc.  now i know it might be a boinc related issue, however, nothing changed.  so whatever i reinstalled the program (knowing that wouldn't work) just incase and that didn't solve the issue.  i've looked all over so this is my last hope.  any suggestions?  

thanks,
ephman

---

### Post by ephman on 2007-05-20
found the solution.  frequency scaling.  i guess on the upgrade to fiesty the setting was defaulted to ondemand.  had to change that up to performance and all is fine.

thanks for the bandwidth,
ephman

---

