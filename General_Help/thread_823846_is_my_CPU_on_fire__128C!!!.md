---
title: "is my CPU on fire?  128C!!!"
date: 2008-06-09
forum: General Help
---

### Post by bluepowder7 on 2008-06-09
so i installed the monitors and two applets (x-sensors and computertemp) to watch my cpu tempteratures since a) it's bloody hot here this time of year, and b) my computer decided to rapidly shut itself down twice over the last few days.

using computertemp (this is the one you can get from berlios or whatever), i get these temperatures:
9191-0290 (1): 35 C *
9191-0290 (2): 38 C
9191-0290 (3): 128 C

using x-sensors, i get:
mobo temp = 35 C
cpu temp = 38 C
temp3 = 128 C

i have no idea what the asterisk (*) is for, and i sure hope that number 3 is not my CPU!!!  it's monitoring an athlon 64 x2 4000 cpu.

so, are the sensors reading one temperature for both cores (and it's 38C)? i have a pretty good thermalright heatsink and if i stick my fingers on the heatpipes (pc cover is off), they're not hot.  the pc is generally able to run 24/7 for quite a while, so maybe my rapid shutdowns aren't heat but cpu overload?  (to clarify - the shutdowns happened when i was running quite a bit video encoding, sys-mon showing both cores being used at 95% and up.  right NOW, it's mostly idle, no encoding, cpu at 5% usage)

anyhoo, the **_main question_** is:

what is 9191-0290 (3) and temp3 actually monitoring?  is my cpu actually at 38 C, which is nice and safe?  what in god's name is at 128C !?!?  can i toss some eggs in there?

---

### Post by Pjotr123 on 2008-06-09
Don't worry: non-existent processors (cores) get this value. You have no third processor/core... The first two readings are accurate.

---

### Post by bluepowder7 on 2008-06-09
ah, good and bad.  good that nothing is about to catch fire.  but i could have used a spot to warm my tea.

i started running some encoding just now, and it looks like the mobo and cpu temperatures are swapped (with cpu cores at around 95% use, the temp is no more than 49C).  is there a file where i can swap the two fields, just to correct it?  i guess some spot in the sensors list...  oh, and remove that silly fire temperature?

---

### Post by Gannon8 on 2008-06-09
> **bluepowder7 said:**
> but i could have used a spot to warm my tea.:lolflag:
Just don't spill it :D

---

### Post by Pjotr123 on 2008-06-09
You can disable the third core in the preferences. Sensors - libsensors - Click on the little triangle to expand the options. I have disabled the second core as well: I only need info from one core, the other one deviates no more than 1 degree Celsius from the first.

---

