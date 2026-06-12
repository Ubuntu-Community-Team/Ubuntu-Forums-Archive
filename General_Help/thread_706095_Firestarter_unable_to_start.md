---
title: "Firestarter: unable to start"
date: 2008-02-24
forum: General Help
---

### Post by dayanandasaraswati on 2008-02-24
while starting firestarter its telling eth0 is not ready and so aborting. I want to enable the port 5900 for VNC activity but firestarter is not starting. Plz help

---

### Post by Beefeater on 2008-02-24
Is eth0 the device in use ..?
This will happen if firestarter starts before your device is ready.
Have you tried
```
/etc/init.d/firestarter restart
```

Some more information about your setup might shed some light.

---

