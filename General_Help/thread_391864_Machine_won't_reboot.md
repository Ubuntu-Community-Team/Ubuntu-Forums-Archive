---
title: "Machine won't reboot?"
date: 2007-03-23
forum: General Help
---

### Post by Rob_Quads on 2007-03-23
I have recently installed 6.10 Desktop onto an old PIII machine which i am going to use as a file server but I have a slight problem. I can't get it to reboot. If I use reboot, shutdown -r, unit 6 ...all end up with the machine turning it self off rather than rebooting.

Anyone have any idea what could be causing this??

Cheers

Rob

---

### Post by hikaricore on 2007-03-23
have you tried:

```
sudo reboot -t now
```

?

Perhaps there's something wrong with your hardware which is not allowing a reboot to occur.

---

