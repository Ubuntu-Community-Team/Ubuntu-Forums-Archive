---
title: "Internet Connection is being cut when Idle"
date: 2013-04-17
forum: General Help
---

### Post by ac98521 on 2013-04-17
So I've noticed here in my Ubuntu 12.04 that whenever I leave my computer idle, say for example I leave my computer steady having a bot on a game continue my game or leave the update manager download huge size of updates, the network connection is being cut. I don't know why. But when I try to enter a site in my browser, it comes back sending byte on my computer again. Why is that?

---

### Post by sanderj on 2013-04-17
... and what kind of Interet connection do you use? For 3G/4G-USB-dongle or other dial-up-connections the above is normal behaviour

---

### Post by ac98521 on 2013-04-18
it is Modem :( DSL

---

### Post by sanderj on 2013-04-18
> **ac98521 said:**
> it is Modem :( DSL

... provided by your ISP? If so, I would call your ISP.

---

### Post by efflandt on 2013-04-18
I would not think that a DSL modem, or whatever connects you to it (ethernet or WiFi?) would go to sleep or disconnect while networking was actively being used (unless there is some other issue that interrupts it).

In **Power** settings in Ubuntu, what is set for "Suspend when inactive for"? If there is no mouse or keyboard activity, your computer might be going into suspend (a low power mode that stops programs, but keeps them in RAM). Or if a laptop, especially on battery, suspend might even be a BIOS setting independent from OS.

---

