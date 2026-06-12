---
title: "Hp pavilion won't boot linux"
date: 2007-08-23
forum: General Help
---

### Post by matthekc on 2007-08-23
hello I want to put ubuntu on my sisters hp pavilion a305w.  I don't get to any linux screens just a plain black screen with a flashing cusor at the top left.  I tried ubuntu and my backtrac disc.  Could this be a bios issue?

---

### Post by DalekClock on 2007-08-23
Have you tried running it in Safe Graphics Mode?

---

### Post by JParkus on 2007-08-23
You could also make sure the bios is set to boot the CD instead of the first HDD

---

### Post by matthekc on 2007-08-23
the cd's don't boot to have the options from grub and yes it is set for a cd boot.  This isn't the first time I have had problems with the older hp's. I wonder if they used to set something funny in the bios? I am thinking of trying to flash them.

---

### Post by DalekClock on 2007-08-23
Perhaps you should try using the Alternate install CD if it doesn't seem to work. Otherwise, you're stuffed unless you have a couple of 'undred to spend on a new machine.

---

### Post by matthekc on 2007-08-23
no we got like ten computers in this family.  I might try the alternate cd thought

---

### Post by Firippu on 2007-08-23
this worked on my hp pavilion a705w,
at the cd boot menu press F6 and add this parameter "linux acpi=off"

if you have a shutdown problem,
add this line to /etc/modules

apm power_off=1

---

### Post by digger95 on 2007-10-15
> **Firippu said:**
> this worked on my hp pavilion a705w,
at the cd boot menu press F6 and add this parameter "linux acpi=off"

if you have a shutdown problem,
add this line to /etc/modules

apm power_off=1

Worked perfectly.  Thank you!

---

