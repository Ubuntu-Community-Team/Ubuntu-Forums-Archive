---
title: "Power drain on HP 14t laptop"
date: 2018-03-30
forum: General Help
---

### Post by erinta on 2018-03-30
I installed 16.04 about a month ago on my HP 14t laptop. Everything seems to work great, except I noticed the battery draining on shutdown when it's not plugged in. I've tried several methods of shutting down including sudo shutdown and sudo poweroff and neither seem to fix the problem. I've also noticed a high pitch whine coming from the front of the laptop near the USB and HDMI ports after powered off, even if nothing is plugged in. Any ideas how to solve this (I'm new to Linux so I'm not sure where to even start)?

---

### Post by erinta on 2018-03-30
I want to add that the whine stops and the battery stops draining if I pull the battery out and put it back. It comes back though with the next power on and shut down. I'm hoping this isn't the only solution though as it's sort of annoying to not be able to just shut down normally.

---

### Post by Yellow Pasque on 2018-03-30
I had a problem with "Wake on LAN" draining the battery on my HP pavilion g7. I forget exactly what I did. Maybe I added this to /etc/rc.local:
```
ethtool -s <interface name> wol d
```

---

### Post by erinta on 2018-03-31
I ran sudo ethtool <device name> and can confirm that Wake on LAN is disabled. So unfortunately that's not my issue.

---

### Post by Yellow Pasque on 2018-03-31
Do you have Windows on this system as well? If so, does that have the same issue?

---

### Post by erinta on 2018-03-31
I had windows on this machine before I installed Ubuntu. It did not have this problem on windows alone. I have, however, since gotten rid of windows so I have no way to test this out any more.

---

### Post by erinta on 2018-04-01
I also want to add that the hum after shutdown seems to be coming from the Ethernet port area. I'm assuming it has something to do with that, but aside from disabling wake on LAN I'm not sure what else to try.

---

