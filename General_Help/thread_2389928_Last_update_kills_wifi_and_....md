---
title: "Last update kills wifi and ..."
date: 2018-04-23
forum: General Help
---

### Post by pmjs1115 on 2018-04-23
After my last update [not the latest but the one before], I get a strange message during boot about not being to recognize graphics hardware. If I get thru it, then Wi-Fi network reports Device not ready.  Hardware is working under a Windows boot or a boot from an earlier Ubuntu on a flash drive. Ideas on how to fix this?

---

### Post by pmjs1115 on 2018-04-27
Two more updates finally fixed this. ???

---

### Post by jeremy31 on 2018-04-27
Sounds like an issue with linux-image-extra not getting installed with the rest of the kernel, check ```
dpkg -l | grep linux-image
```

---

### Post by pmjs1115 on 2018-04-28
Turns out I was wrong; not solved; changed. uname shows 4.4.0-122-generic #146-Ubuntu SMP and the dpkg command shows lots of extras with the latest being 4.4.0-122.146.
My latest symptom is that wifi comes up fine if the network has a wired connection during boot. Without that connection, wifi shows device not ready.

Still looking for ideas.

Paul

---

