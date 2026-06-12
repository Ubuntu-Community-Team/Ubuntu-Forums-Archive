---
title: "Uby 5.04 booting on HP Pavilion desktop"
date: 2005-06-17
forum: General Help
---

### Post by Bandit on 2005-06-17
I downloaded the Ubuntu 5.04 i386 ISO and burned it at 4x.
When I start to boot it on my wifes HP Pavilion desktop it boots up to the point where you press enter to finish the booting of the live CD and then it just reboots the PC and loads the same screen again.
I forgot the exact model of her PC, its a Walmart special with Intel everything and a 2.1Ghz Celeron.
Is there anything special I have to do to get it to work on her PC.
I would really like to get her away from winders...
Thanks,
Joey B)

---

### Post by intangible on 2005-06-17
[QUOTE=Bandit]I downloaded the Ubuntu 5.04 i386 ISO and burned it at 4x.
When I start to boot it on my wifes HP Pavilion desktop it boots up to the point where you press enter to finish the booting of the live CD and then it just reboots the PC and loads the same screen again.
I forgot the exact model of her PC, its a Walmart special with Intel everything and a 2.1Ghz Celeron.
Is there anything special I have to do to get it to work on her PC.
I would really like to get her away from winders...
Thanks,
Joey B)[/QUOTE]
 Try this at the boot prompt of the installer: **linux noapic nolapic**.  If that doesn't work, on the next boot, press F5 for some additional options you can try.  It sounds like a peice of hardware is causing it to fail, if you can troubleshoot it, you should be able to work around whatever is locking it up.

---

### Post by Bandit on 2005-06-17
Kewl, I will try that....
I think when I tried it I was getting the syntax down wrong..

---

### Post by codejunkie on 2005-06-17
try| live acpi=off |for the live cd and| linux acpi=off |for the installation disk.

---

