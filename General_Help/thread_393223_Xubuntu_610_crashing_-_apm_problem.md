---
title: "Xubuntu 6:10 crashing - apm problem"
date: 2007-03-25
forum: General Help
---

### Post by tictacman on 2007-03-25
Lately my system has become very unstable.  Earlier in the week I had a problem when searching for an artist in banshee  the whole system froze I couldn't even turn the caps lock light on and off on the keyboard.  I removed banshee, but the system continues to freeze up only now its a soon as I move the mouse in xfce.

When I looked at /var/log/messages I noticed that the system freezes coincided with these lines

Mar 24 11:13:23 lounge kernel: [17179618.124000] apm: BIOS not found.
Mar 24 14:05:23 lounge kernel: [17179617.176000] apm: BIOS not found.
Mar 24 14:31:17 lounge kernel: [17179618.512000] apm: BIOS not found.
Mar 24 16:50:20 lounge kernel: [17179618.392000] apm: BIOS not found.
Mar 25 06:45:10 lounge kernel: [17179617.156000] apm: BIOS not found.
Mar 25 07:00:25 lounge kernel: [17179618.688000] apm: BIOS not found.
Mar 25 08:13:01 lounge kernel: [17179756.528000] apm: BIOS not found.
Mar 25 17:22:47 lounge kernel: [17179617.796000] apm: BIOS not found.
Mar 25 18:00:37 lounge kernel: [17179619.196000] apm: BIOS not found.
Mar 25 18:06:16 lounge kernel: [17179619.620000] apm: BIOS not found.
Mar 25 18:32:33 lounge kernel: [17179619.132000] apm: BIOS not found.

I can't find any reference to apm in power section of the bios.  Do I really need apm and can I stop xubuntu looking for it?

Also the bios startup screen reads acpi compliant - which might have some relevance here.

---

### Post by tictacman on 2007-03-27
Oh well I think its mobo problem, works for a while before crashing and i'm even having a hard time to get the bios up.  Guess I'll trash the board and try again.

---

