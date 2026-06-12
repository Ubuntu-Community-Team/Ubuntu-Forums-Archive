---
title: "Auto reboot..."
date: 2008-04-24
forum: General Help
---

### Post by Aquastus on 2008-04-24
Hello.
I have this weird problem on my pc. Whenever I shut it down (I at least clicked "shut down") it starts up again. Sometimes it happens right after it has shut down. Sometimes it starts up randomly in about an hour or more after shut down. This started happening after I installed Ubuntu (didn't happen before with Vista)
So far this hasn't happened when I'm sleeping, but it is still annoying and even a little scary when it just starts up like that randomly.
Why does this happen? Is this some kind of known bug, or is it just me?

---

### Post by Ub1476 on 2008-04-24
It's just you:)




Alright, I never heard of this before. Have you checked if there's anything abnormal in BIOS?

Here's a link which migh help:
[http://www.techsupportforum.com/hardware-support/ram-power-supply-support/138423-computer-randomly-starts-back-up-after-shut-down.html](http://www.techsupportforum.com/hardware-support/ram-power-supply-support/138423-computer-randomly-starts-back-up-after-shut-down.html)

---

### Post by Aquastus on 2008-04-24
Exactly what do you mean by abnormal? I'm not sure what to look for.
I doubt that this is about the power supply because that was changed recently. (Then again it may be because of the power supply because it's new. Can a power supply be incompatible with Linux?)

---

### Post by Shazaam on 2008-04-24
What Ub1476 is saying is WOL (Wake on Lan) might be enabled or a "wake on mouse (or keyboard) event" has been enabled. I once had that happen (pc was off, moved mouse and pc started). Check your bios settings (especially Power settings).

---

### Post by Aquastus on 2008-04-25
Well I checked under Power Management > Set Wake Up Events... and I found that Resume On PME# was enabled.  What does that mean?

---

### Post by Aquastus on 2008-04-27
> **Aquastus said:**
> Well I checked under Power Management > Set Wake Up Events... and I found that Resume On PME# was enabled.  What does that mean?
OK, I disabled it and it didn't help. Everything else is disabled too.

---

### Post by ghost_ryder35 on 2008-04-27
If everything in your BIOS for wake on lan is disabled and wake on lan is disabled, then check for faulty wiring behing the power button on the case and or check to make sure your not having electrical surges causing the computer to boot.

---

