---
title: "Network/shutdown issue"
date: 2007-10-28
forum: General Help
---

### Post by wheredidrealitygo on 2007-10-28
I'm not a beginner, but I'm stumped for a few problems I've been having. Let me know about any log files I can provide. Relevant system specs are in sig :)

1. When I click shutdown (with or without compiz running) everything freezes except my mouse. Also when I hit alt-ctrl-del to log out. I can manually do a "gksudo shutdown -r (or -P) now" and it'll restart (or shutdown) just fine. I'm wondering if a ```
noapic nolapic
``` added to the grub menu could fix this, or if it could be the nvidia card. Using the restricted driver.

2. Maybe having to do with the problem mentioned above, the shutdown graphic sequence with the orange bar only happens for about three to four seconds after I get about four lines of text saying something about the networkmanager. This happens with or without eth0 or wlan0/wmaster0 active.

3. Wireless will drop out randomly, it's rt73usb (Ralink), I've followed a LOT of other threads on this particular subject before posting myself, and none seem to work (including disabling ipv6 in OS and firefox). I'm getting another ethernet cord next week anyway, so it doesn't matter too much.

Looking forward to any suggestions :)

---

### Post by wheredidrealitygo on 2007-10-30
Upon a little more exploration, and the removal of the "powernowd" package, it only remains frozen (after clicking shutdown) for about 2 - 3 minutes, then the shutdown options (logout, sleep, shutdown, restart, etc) will appear and I can shutdown normally.

Bumpage?

Any logs I can provide (when I get home from work) let me know :)

---

### Post by steveneddy on 2008-02-08
what ever happened with this? I am having the same problem and trying not to reinstall if possible.

---

### Post by wheredidrealitygo on 2008-02-08
I ended up reinstalling and it eventually fixed itself on this install :???:

---

