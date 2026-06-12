---
title: "Sound Problem ALC850"
date: 2008-05-19
forum: General Help
---

### Post by Mishkafofer on 2008-05-19
Hi all
Yet another cry for help from Linux noob about his Sound.
I got Ubuntu 8.04 64Bit.
Since version 6 i dont got sound (rarely used Ubuntu, i am student so no free time for Linux study) but finally version 8 seems very good.
In sound preferences i found out that my Sound device is recognized (It didnt in 7 version) as Realtek ALC 850 rev 0, everything is marked as ALSA.
When i press TEST button is dont get error message but still no sound.
I clicked unMute but it wasn't muted.
What might couse the problem.
Mobo: GA-K8N51GMF-RH

---

### Post by Mishkafofer on 2008-05-19
Guess what, it was mixer mute. Apparently i got mixers for sound cards that dont exists, funny but the mixer that works is for Intel ICH and Realtek mixer dont work (i got realtek chip ALC850).

---

