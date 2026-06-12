---
title: "USB serial port name changes"
date: 2013-11-20
forum: General Help
---

### Post by jimspruell on 2013-11-20
sometimes name changes from /dev/ttyACM0 to /dev/ttyACM1,2,3,4 (now up to ACM8)

happens sometimes when (not always) I unplug and replug device (Freescale KL25Z development card)

why and how can I change it back to ACM0?

---

### Post by ian-weisser on 2013-11-20
Create a udev rule in /etc/udev/rules.d that sets the name (or does some other action you wish).
Many examples in that directory.

---

