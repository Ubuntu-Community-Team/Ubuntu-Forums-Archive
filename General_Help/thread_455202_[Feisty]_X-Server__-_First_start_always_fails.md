---
title: "[Feisty] X-Server  - First start always fails"
date: 2007-05-26
forum: General Help
---

### Post by Stalafin on 2007-05-26
I have a weird problem when starting Feisty:
Every time I start my computer and Feisty starts loading up, I get an error message similar to this one:
> (WW) NVIDIA: No matching Device section for instance (BusID PCI:3:0:0)
(EE) No devices detected

fatal server error:
no screens found

The blueish error screen appears and tells me that there is something wrong. I press the reset-button and, oh wonder, everything is alright and the X-Server starts up correctly.

If I don't turn off the computer I can restart it as often as I want and the X-Server doesn't encounter any problems. But if I try to switch the computer on after having powerer it off I will always get the error message.
I have absolutely no idea where this error comes from.
I am using the default restricted nVidia driver that come with Feisty (the one you have to enable in the Restricted Drivers Manager).

I have attached both the Xorg log-file from the failed start-up and the Xorg log-file where everything worked out correctly (the first - Xorg.0.log.old - is 'fresh', at the end of the file you will find the error messages; the second one - Xorg.0.log - is in use in the current session so that it is a bit bigger).

---

### Post by b3tzi on 2007-05-26
I have the same problem. :(

---

### Post by Stalafin on 2007-05-27
Hey b3tzi! Good to know I am not the only person with this problem.

What is your computer's configuration?
Mine:
Mainboard: Abit NF-M2 nView (nForce 430 AND GeForce 6150 graphics)
CPU: AMD Athlon 64 X2 3800+ EE
Graphics: nVidia GeForce 7600GT
RAM: 2048MB g.skill PC6400

I am figuring if this problem is caused by the two graphics cards I have in my computer (dedicated and integrated).
I am going to see whether turning of the integrated card in the BIOS will solve it.

---

### Post by b3tzi on 2007-05-27
> **Stalafin said:**
> I am figuring if this problem is caused by the two graphics cards I have in my computer (dedicated and integrated).
Same here.
I could solve the problem by rebooting my computer after I get that "no screen found" error.

---

