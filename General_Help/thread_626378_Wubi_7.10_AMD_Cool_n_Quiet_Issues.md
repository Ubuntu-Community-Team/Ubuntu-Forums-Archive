---
title: "Wubi 7.10 AMD Cool n Quiet Issues"
date: 2007-11-29
forum: General Help
---

### Post by hattawayd on 2007-11-29
I was having issues installing Gutsy Wubi.
Symptoms:
On reboot to begin Ubuntu Install.
Boot process starts, kernel loads, but then after some time my computer goes to sleep and will not respond (monitor goes into low power state)

I rebooted and chose option 3, verbose
I saw the system hang forever on Staring powernowd

I rebooted the system, went into bios and disabled "Cool n Quiet"

I was then able to finish the install.
Once installed I removed powernowd and reenabled "Cool n Quiet"

Things seem to be working so far. Just thought it might be useful for debugging, although it would be nice to get powernowd working.

---

### Post by ago on 2007-11-29
Suspend/hibernation do not work in wubi

---

