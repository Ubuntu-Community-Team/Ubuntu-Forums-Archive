---
title: "How to debug a system freeze"
date: 2008-06-08
forum: General Help
---

### Post by superdif on 2008-06-08
Hi all,
in the last 3 days my computer keep freezing (some time after 2 minutes, some time after 2 hours) and I am always forced to push the reset button.

While it always happen while playing World of Warcraft, I would like to do a deeper test to find the cause before blaming Wine.

Tonight I will do a memtest (since it takes a lot of time I'll run it while I sleep), but in the meantime I could do some other test.

What test can I do?

Thank in advance.

---

### Post by superdif on 2008-06-14
I really need to get an answer: my system keep freeze every 15-45 minutes and I am tired to reset and wait for the reboot. ](*,)

Since my original post I already did a RAM test (I have run memtest for 8.5 hours and found no problems) and disabled compiz (purged from Adept Manager) so I can exclude these two possible cause.

I also re-installed Kubuntu from scratch to clean any broken program/library/whatever may interfere.

---

### Post by VMC on 2008-06-14
How is WOW launched. Through Wine or someother emulation? Try and start it through the Terminal ... I just realized that won't work because you said it froze. Any indication reading the System Log files. Maybe you can find help there.

---

### Post by superdif on 2008-06-16
I am using Wine.

So far I checked:
/var/log/messages
/var/log/syslog
/var/log/Xorg.0.log
dmesg
but every time I found no clue. :confused:

---

### Post by superdif on 2008-06-20
No ideas? :(

---

### Post by legine on 2008-07-31
I'd guess it is the Nvidia card got some misshap.

Have you tried other 3d games? (preferable nativ linux)

try tomatoes or tuxracer, if those crash too you at least know it is not wine.

doom3 has also a linux version if you own that one. Or netherwinternight 1.

GL!

---

