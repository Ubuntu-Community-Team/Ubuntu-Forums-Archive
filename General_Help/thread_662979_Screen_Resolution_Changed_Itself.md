---
title: "Screen Resolution Changed Itself"
date: 2008-01-09
forum: General Help
---

### Post by dbsoundman on 2008-01-09
My Ubuntu 7.04 just randomly changed the Screen Resolution parameters today when I started up the computer, and won't let me set the resolution back to 1024x768. Right now the highest option is 800x600. With my old LCD monitor I had a higher resolution than 1024...I think it was 1280 by something, but this monitor only goes up to 1024. Now, I can only get it up to 800 for some reason. What happened? I don't think I changed anything with this temporary crap-tastic LCD monitor I'm using, but I will check that out. Any tips?

-Dan

---

### Post by dcstar on 2008-01-09
> **dbsoundman said:**
> My Ubuntu 7.04 just randomly changed the Screen Resolution parameters today when I started up the computer, and won't let me set the resolution back to 1024x768. Right now the highest option is 800x600. With my old LCD monitor I had a higher resolution than 1024...I think it was 1280 by something, but this monitor only goes up to 1024. Now, I can only get it up to 800 for some reason. What happened? I don't think I changed anything with this temporary crap-tastic LCD monitor I'm using, but I will check that out. Any tips?

-Dan

Reboot with the monitor powered on and make sure that the X server detects your card/monitor correctly.

---

### Post by Helios38 on 2008-01-09
if your monitor supports widescreen, go to System > screens and graphics.

then click on the monitor sectection bar (whatever u call it) and it will open a window to choose your monitor, there should be a box, about enabling widescreen. enable it only if your monitor supports it.


also, check to see if your graphics card is identified correctly.


i'm sorry if this doesnt help but i've seen problems like this on other forums and im just repeating their responses ;)

---

### Post by dbsoundman on 2008-01-09
Thanks for the info. Restarting the computer did the trick. I have to unplug this monitor when I shut down at night because the crappy built-in speakers make odd noises and are really noisy. So I just need to remember to plug in the monitor, then turn on the computer. I'm counting down the days until I can get a new monitor...

-Dan

---

### Post by dcstar on 2008-01-09
> **dbsoundman said:**
> Thanks for the info. Restarting the computer did the trick. I have to unplug this monitor when I shut down at night because the crappy built-in speakers make odd noises and are really noisy. So I just need to remember to plug in the monitor, then turn on the computer. I'm counting down the days until I can get a new monitor...

-Dan

If you restart Ubuntu without a working monitor connected, it cannot determine what to do so it defaults to the base resolution.

---

