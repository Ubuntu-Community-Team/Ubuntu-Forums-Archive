---
title: "System Freeze!"
date: 2005-05-09
forum: General Help
---

### Post by i-tech on 2005-05-09
Hi all;
My system freezes from time to time i couldnt figure out why because not related with any specific software. But whenever i try to install planeshift (the online game) it freezes in the installation menu. or somethimes when i started amarok or all of sudden it freezes? ](*,) any solutions that you can suggest?

---

### Post by tread on 2005-05-09
If there is no indication about why it freezes (any particular application etc.) I would probably start with:

1. Check /var/log/messages after a freeze
2. Check the Xorg log files (I don't know where they are) after a freeze

---

### Post by cutOff on 2005-05-09
> **i-tech]Hi all said:**
> (*,) any solutions that you can suggest?
it happens to me sometimes when I use firefox.

Any clue??

---

### Post by pirast on 2005-05-09
It happenes hero, too..

While using

- Firefox
- Evolution
- Synaptic

as I know. System:
Motherboard: PC-Chips M848A
CPU: Athlon XP 2600+ (256kb cache version)

I exchanged everything excepting the cpu and the motherboard.

Martin

---

### Post by rosslaird on 2005-05-09
[QUOTE=pirast]
Motherboard: PC-Chips M848A
CPU: Athlon XP 2600+ (256kb cache version)

I exchanged everything excepting the cpu and the motherboard.

Martin[/QUOTE]

If your motherboard is like mine, then you may have an onboard nvidia video setup. If that's the case, you are likely experiencing the nvidia-xorg lockup bug that so many people have complained of (search for the numerous posts on this forum about the issue). Basically, you could try disabling RenderAccel in your xorg.conf file:

"Option"  "RenderAccel"  "false"

And disable the Composite extensions if you have them (though this is a smaller issue).

Cheers.

Ross

---

### Post by cutOff on 2005-05-09
Ok I forgot to put more data

Box: Athlon XP 1800+
SO: Ubuntu Hoary (latest release)
Graphics card: Nvidia Geforce mx440 (with Nvidia drivers)

---

### Post by rosslaird on 2005-05-09
[QUOTE=cutOff]Ok I forgot to put more data

Box: Athlon XP 1800+
SO: Ubuntu Hoary (latest release)
Graphics card: Nvidia Geforce mx440 (with Nvidia drivers)[/QUOTE]

Yup, it'll be the nvidia drivers.
Either downgrade to the 6* series, or just disable renderaccel.

---

### Post by i-tech on 2005-05-09
My system is intel p4 2.4 and graphics card is ATI Radeon 9600XT. So I guess not related with nvidia ;-)

---

### Post by pirast on 2005-05-09
I have an ATI card with "ati" drivers. 
"Option" "RenderAccel" "false" or simular options didn't work so now I am using the "vesa" driver and my system doesn't freezes.

Thanks


Martin

---

