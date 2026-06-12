---
title: "laptop locked into airplane mode after ubuntu install 22.04"
date: 2022-05-25
forum: General Help
---

### Post by smallville1979 on 2022-05-25
the old laptop had an issue installing windows 7 where the nic driver wouldnt install. 
I installed unbuntu 22.04 now it shows as locked in airplane mode. 
I have no idea how to turn it off and if you run the command it shows as hardblocked. 
is there any fix?

---

### Post by grahammechanical on 2022-05-25
Hard blocked usually means that the WiFi electronics adapter is switched  off. We can check the BIOS/UEFI to see if it is disabled and correct  the situation. What have you tried to correct this? System  Settings>WiFi has sliders that turn WiFi and Airplane mode Off and  On. Are you saying that these sliders cannot be moved to the On  position?

As this is an old laptop how efficient is the battery?  Is it holding its charge? The OS may be switching WiFi off because the  battery charge is so low. It is also possible that the WiFi adapter is  broken. Have you considered that? You may need to think about buying an  USB WiFi adapter.

Regards

---

### Post by #&amp;thj^% on 2022-05-25
try with:
```
sudo rfkill unblock all
```
If that doesn't work show us this:
```
rfkill list all
```

---

### Post by DuckHook on 2022-05-26
*Thread moved to **General Help** as the more appropriate forum.*

---

