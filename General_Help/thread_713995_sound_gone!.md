---
title: "sound gone?!"
date: 2008-03-03
forum: General Help
---

### Post by jrockpunk1 on 2008-03-03
k so i turned my computer off, and when it came back on the sound isnt working. when i click the volume bar it comes up with an error saying:

```

No volume control GStreamer plugins and/or devices found.

```
whats happened? and what should i do?

---

### Post by ibuclaw on 2008-03-03
I'll ask questions later, but I ask you to try this first:

1) Check that ubuntu-linux-modules is installed through synaptic. (Usually generic)
If it isn't install it and reboot.

2) Check that you're an audio group member. Sometimes it automatically switches from on to off.
This can be checked in System>Admin>Users&Groups
Clicked on your user and click "Properties" and under "User Privileges" tab, check, uncheck and check the "Use Audio Devices" tick box.
Then restart X and hope for the best.

---

