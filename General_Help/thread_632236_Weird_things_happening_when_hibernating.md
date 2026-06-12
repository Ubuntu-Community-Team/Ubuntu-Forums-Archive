---
title: "Weird things happening when hibernating"
date: 2007-12-05
forum: General Help
---

### Post by MONODA on 2007-12-05
whenever I try to hibernate I see my screensaver for  half a second and then my monitor turns off but the power button and everything else stay on. So I wait for a long time and nothing happens. So I force a shut down and turn my comouter back on. Once Ubuntu loads I see the screen that I see when I lock my computer. What is going on???

---

### Post by MONODA on 2007-12-05
also when i turn my computer back on the loading screen shows up but the loading bar does not move and when i first hibernate my screen does that thing a tv does when there is no reseption for like half a second. Anyone else having this problem???

---

### Post by khurrum1990 on 2007-12-05
Hi, can u please post ur system specs in detail. Also whether ur vga card is agp, pci, or pci-express? R u running Compiz Fusion or Beryl as well?

---

### Post by khurrum1990 on 2007-12-05
try adding:
Option NvAGP    "1"
in /etc/X11/xorg.conf under the device section then reboot ur pc and try hibernate after turning off compiz fusion or beryl.

---

### Post by MONODA on 2007-12-05
could you tell me exaclty what i should put in my xorg.conf file. maybe even an example of what it should look like. thanks.

---

