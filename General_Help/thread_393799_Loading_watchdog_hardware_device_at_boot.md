---
title: "Loading watchdog hardware device at boot"
date: 2007-03-26
forum: General Help
---

### Post by Kommius on 2007-03-26
Hi everyone!

I'm almost done writing a tutorial explaining how to install watchdog (hardware & software) for Ubuntu, if your mother board has a watchdog chipset.

However, i'm stuck on one last part of the tutorial, which is loading the kernel module when the system boots..

What i do to manually load the kernel is a **modprobe w83697hf_wdt wdt_io=0x4**, but how can i implement that in the **modprobe.d** folder so the drivers are loaded automatically at startup?

Thanx for any help anyone can provide! :)

---

### Post by rand76 on 2007-04-13
Not sure if this is the exact info you need but if you put an entry in /etc/modules it should load the module at startup.

---

