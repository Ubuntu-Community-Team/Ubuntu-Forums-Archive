---
title: "LIRC and MythTV"
date: 2008-05-22
forum: General Help
---

### Post by rxtx on 2008-05-22
Hi there-

I'm having a problem with MythTV and LIRC. Not all buttons on my remote work, but when the event capture is initialised with the following command, 

```
sudo /usr/sbin/lircd -H dev/input -d /dev/input/event4 -n &
```

THEN Myth frontend is started, all is well.

I have tried to get this to run at boot time via .gnomerc, but it doesn't seem to have the desired effect.

I also seem to have an odd occurrence on an lircd restart with init complaining that lircd fails when stopping, but is reported ok on loading and starting.

I'm stumped. Any help?

---

### Post by rxtx on 2008-05-27
*bump* Anybody? Any ideas?

---

