---
title: "Which log to see what's causing my hard drive to &quot;grind away&quot;"
date: 2021-02-20
forum: General Help
---

### Post by cforput on 2021-02-20
Ubuntu Mate 20.04
Acer Aspire F15 F5-573G-56CG
Intel i5-6200U
NVidia GForce

After my computer goes to sleep or I close the lid and then come back to it, it's completely hung up. The monitor won't come back on and I can hear my hard drive "grinding away". Almost like a virus scanning program that is so intensive that nothing else works. Until the last time it happened, I'd hard boot by holding the power button down. But, the last time, I thought to myself, "the computer is doing something, just wait". So, I waited. I just left the laptop alone and went and did some other stuff. About 4 hours later, I checked on it and it was "freed up" and working again. I've rebooted since so I assume I've lost any log information that might tell me what's going on. The next time it happens, I plan to leave it along again until it finishes whatever it's doing. Once that happens, what logs or other tools would you suggest I review to see if I can figure out why it's doing this?

---

### Post by ActionParsnip on 2021-02-20
Run:
```

dmesg | tail 

```
and it may give clues

---

### Post by CatKiller on 2021-02-20
It sounds to me like you're running out of RAM during the resume process for some reason.

---

### Post by mikewhatever on 2021-02-20
> **CatKiller said:**
> It sounds to me like you're running out of RAM during the resume process for some reason.

+1, there isn't any RAM according to the specs above. :)

---

### Post by cforput on 2021-02-20
NVidia card has 4GB dedicated VRAM and an additional 8 GB DDR4 RAM too

---

