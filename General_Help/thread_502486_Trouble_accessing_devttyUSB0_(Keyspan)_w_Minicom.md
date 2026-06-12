---
title: "Trouble accessing /dev/ttyUSB0 (Keyspan) w/ Minicom"
date: 2007-07-16
forum: General Help
---

### Post by djtopper on 2007-07-16
Just got the minicom package and configured it to point to /dev/ttyUSB0.  Unfortunately, I get nothing when I fire up my little external SBC device (which works fine on my Mac).  My kernel does show the device:

Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 06cd:0121 Keyspan
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

But minicom can't seem to see anything coming through.  Is there another program I might check out?  Any other debugging tips?  Not much posted on this it seems.

Thanks,

D

---

### Post by djtopper on 2007-07-18
Well, a reboot seems to have solved the problem.  Strange.

D

---

