---
title: "Olympus VR-350 camera only mounts w/o SD card"
date: 2014-11-28
forum: General Help
---

### Post by lykwydchykyn on 2014-11-28
My son got an Olympus VR-350 camera for his birthday.  His laptop runs Lubuntu 14.04.

When we plug in the camera without an SD card inserted, it mounts fine and we can pull off the pictures without any problems (looks like it acts like a regular USB drive, doesn't use mmc).  If we plug it in with the SD card in, the device never shows up.  dmesg shows a number of read errors:

```

[   20.631908] sd 2:0:0:0: [sdb] Unhandled sense code
[   20.631914] sd 2:0:0:0: [sdb]  
[   20.631918] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   20.631923] sd 2:0:0:0: [sdb]  
[   20.631926] Sense Key : Medium Error [current] 
[   20.631933] sd 2:0:0:0: [sdb]  
[   20.631938] Add. Sense: Multiple read errors
[   20.631943] sd 2:0:0:0: [sdb] CDB: 
[   20.631946] Read(10): 28 00 00 00 00 00 00 00 08 00

```

Tried formatting the card, but it didn't make any difference.  Card works fine in the camera, and I can remove it and plug it into a card reader (his laptop doesn't have one, alas) and remove pictures without a problem, so I think the SD card is fine (It's brand new, anyway).

Anyone have any wisdom here?

---

