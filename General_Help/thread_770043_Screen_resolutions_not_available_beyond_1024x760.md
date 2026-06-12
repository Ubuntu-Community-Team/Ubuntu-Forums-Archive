---
title: "Screen resolutions not available beyond 1024x760"
date: 2008-04-27
forum: General Help
---

### Post by akshar_patel_47 on 2008-04-27
I just installed Hardy Heron and it's cool except for the fact that it doesn't show me screen resolutions beyond 1024x768 in the monitor resolution setting.
I used to run Gutsy Gibbon on 1280x968.
The command sudo dpkg-reconfigure xserver-xorg also does allow me to choose my screen resolutions which we could do so in Gutsy.

Can anyone help me out please?

I have Intel core 2 duo 2.2 ghz
Nvidia 8500GT graphics card if this information is of any help.

---

### Post by PinkFloyd102489 on 2008-04-27
Install nvidia-settings and change the resolution from there. Note that you'll have to run it with gksudo.

---

### Post by jonnyrab on 2008-04-27
Yeah my resolution only goes up to 800x600. It was nice when i could use dpkg-reconfigure... anybody have any solution to this

---

### Post by akshar_patel_47 on 2008-04-27
Thanks... Using nvidia settings did solve my problem. But what has happened to dpkg-reconfigure? Why doesn't it now allow us to choose screen resolutions and graphic card drivers which it did uptill now?

---

### Post by Zorael on 2008-04-27
> **akshar_patel_47 said:**
> Thanks... Using nvidia settings did solve my problem. But what has happened to dpkg-reconfigure? Why doesn't it now allow us to choose screen resolutions and graphic card drivers which it did uptill now?
It doesn't? It should, unless you include the -phigh argument.

---

### Post by renz on 2008-04-27
I have an HP 6510b laptop and it seems to be working fine under the new Hardy install including compiz. I too have a limit on the resolution of 1280x800. I'm using the integrated Intel graphics chipset. (Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller) Can't find Linux specific drivers from Intel. Any suggestions?

renz

---

