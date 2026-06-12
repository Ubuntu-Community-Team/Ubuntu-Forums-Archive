---
title: "Shut Down Freezes"
date: 2007-06-10
forum: General Help
---

### Post by churgin on 2007-06-10
I am running FF, and in general enjoying it, however the Shut Down dosen't complete. I read in other places that there were also problems with Hibernate etc., but on my system...which seems fine except for shutting down to a flashing screen...works.

Any ideas?

Neil

---

### Post by Cod on 2007-06-11
Unfortunately I have no advice to give, only that I am suffering the same problem.  I was running Edgy and all was fine.  Last night I upgraded to Feisty and my machine no longer completes the shut down.  It does nearly everything, but then hangs at the last with the Ubuntu logo on a black screen.

It may be connected but since upgrading I'm also getting a weird loading error, something about BIOS fails cut off (2000), force ACPI.  My machine is from 1999 so the BIOS does fail the cut off year but Edgy never used to complainand I never knew that there was a cut off year.

I'll scout about for help and post here if I fins anything.

---

### Post by Cod on 2007-06-12
After rummaging through the forums I found this fix:

Edit /etc/modules i.e.:

sudo gedit /etc/modules

then add a new line with the following statement:

apm power_off=1

then save and reboot.

The shutdown now completes fully.  Hope this helps

---

### Post by greggr on 2007-10-06
I have been running Ubuntu successfully beginning with 5.10 (Badger).  For a long time I have been running 6.06LTS without any major problems.  Starting with 7.04 (and now with the beta 7.10)  it fails to shut down and hangs in the last sequence screen. This is really annoying regression.  I'm stuck using 6.06 unless they fix this bug 'cause a powerdown is my only option... and that eventually corrupts everything. I am running a legacy mutt,  Epox 8kta3 M.B. AMD Althon VIA KT 133 chipset 384MB 750HZ with in the neighbohood of 18 of 20 GB free.  I use a 350w Powerman ps.  Clues as to when they will fix this ongoing bug?

---

### Post by greggr on 2007-10-08
Fixed this one after seeing several references to older BIOS systems.  You might check your "ACPI Function" setting under "Power Management" in the BIOS.  Mine was set to "Disabled".  Setting it to "Enabled" which reads "Support ACPI function for new OS" worked like a charm.  All is well again in Linuxland   G.

---

