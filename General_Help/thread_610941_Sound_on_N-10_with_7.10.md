---
title: "Sound on N-10 with 7.10"
date: 2007-11-12
forum: General Help
---

### Post by dlbrando on 2007-11-12
Ok I still have no sound on my emachines n-10.  the drivers I have downloaded from nvidia are being rejected.  Does anybody have a driver or know of a good fix.  I have yet to get sound working properly.  7.10 doesent seem to have the feature to turn surround on that works for other users.  and when I query it for the hardware installed a generic nvidia listing comes up.  Under system I looked at the hardware list and came up with this

MCP51 PCI-X GeForce Go 6100

this is the card that is listed for a lot of different stuff listed under hardware.  I am thinking maybe a driver problem that affects only sound???

---

### Post by ddrichardson on 2007-11-12
Sound doesn't work on the N-10 or N-12. All the hardware is nVidia, the soundcard is MCP51 Intel HDA Rev 2. There are bug reports with ALSA and yet there has been no progress since 2006 when it was reported.

This has been a perennial source of annoyance, recompiling ALSA with various patched has so far only got me as far as a high pitched whine from the card. The problem is not rectifiable by altering alsa-base or recompiling ALSA because its to do with the Sigmatel modem interfering with the operation of the card - the configuration being slightly different from just about every laptop with this soundcard.

Sorry I can't offer anything more helpful, but ALSA is working on it, it just seems the other notebooks are getting more of a push than the Gateway/eMachines.

---

### Post by dlbrando on 2007-11-12
ok, thans for the reply, now I can focus on other problems and hope als solves this one for me

---

