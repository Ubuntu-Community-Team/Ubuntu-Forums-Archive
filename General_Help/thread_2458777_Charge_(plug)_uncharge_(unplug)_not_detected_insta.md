---
title: "Charge (plug) /uncharge (unplug) not detected instantly"
date: 2021-03-03
forum: General Help
---

### Post by paolo18 on 2021-03-03
Hi friends, I installed Ubuntu 20.04.2 LTS on my Lenovo Ideapad S145-15IIL and I got everything working well except the fact that once I plug in the ac adapter to charge the laptop, it's not immediately recognized but there's a delay of 30/40 seconds. The same if I unplug it: the icon of the battery remains "on charging status" for 1 minute too until changing to normal status. 
How can be this be possibile? Anyway to fix this behiavour?
Thanks.

---

### Post by CelticWarrior on 2021-03-03
Update the firmware (UEFI) before anything else.

---

### Post by paolo18 on 2021-03-03
> **CelticWarrior said:**
> Update the firmware (UEFI) before anything else.
Do you mean BIOS update?

---

### Post by CelticWarrior on 2021-03-03
No, I meant UEFI update. BIOS isn't used in (almost) any new computer from ~2010 or newer. Unfortunately many manufacturers and users insist in using the now wrong name "BIOS" for the motherboard's firmware.

---

### Post by paolo18 on 2021-03-03
> **CelticWarrior said:**
> No, I meant UEFI update. BIOS isn't used in (almost) any new computer from ~2010 or newer. Unfortunately many manufacturers and users insist in using the now wrong name "BIOS" for the motherboard's firmware.
My firmware is still updated to the lastest version...

---

### Post by CelticWarrior on 2021-03-03
> **paolo18 said:**
> My firmware is still updated to the lastest version...

Great, so there's nothing else to do, for the moment. This may or may not be addressed in a future UEFI update. Probably not because it isn't really a problem. Maybe an annoyance but definitely not a problem, all laptops have some delay in detecting the charger.

---

### Post by grahammechanical on 2021-03-03
A suggestion that is not based on any experience with a UEFI motherboard. Enter the UEFI settings utility and look for a section on the battery charge state. Then see how long the motherboard sensors take to detect the charger being plugged in and out.

It is my guess that the operating system is in some way reading the motherboard sensors through the UEFI settings utility rather than accessing the hardware sensors directly.

Regards

---

### Post by Impavidus on 2021-03-04
What does /sys say about the status of your power? This may be a bit hardware dependent, but on my laptop I can see it at```
cat /sys/class/power_supply/AC/online
```If it returns 1, it's plugged in, if 0, it's not. Maybe it's only your GUI that's a bit sluggish.

---

