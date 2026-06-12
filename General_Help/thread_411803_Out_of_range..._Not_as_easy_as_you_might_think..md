---
title: "Out of range... Not as easy as you might think."
date: 2007-04-17
forum: General Help
---

### Post by dv5237 on 2007-04-17
I tried to install Ubuntu on my school PC so i could show the people on my school how easy it is to work whit Ubuntu. The problem comes when the live CD is fully booted i get a "out of range" message on my screen. Its a TFT and default set on 1024x768 @ 75 hz. I tried to change i can change it too 800x600 @ hz but that just looks crappy. I changed the TFT whit another one of the same brand but got the same results. Then i changed it whit a CRT and that worked perfect. But since everyone has a in the classroom it doesn't really looks inviting when i put a big CRT on my desk. As last is tried the change the xorg.conf but after a hour without any succes is booted back to windows. 

Could this be the TFT or my VGA-card?

---

### Post by heimo on 2007-04-17
I'd bet it tries to output too high refresh rate to the monitor. You could probably fix this by reconfiguring Xorg using these instructions:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Or this howto:
[HOWTO: Solving resolution/refresh rate problems in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by dv5237 on 2007-04-17
> **heimo said:**
> I'd bet it tries to output too high refresh rate to the monitor. You could probably fix this by reconfiguring Xorg using these instructions:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Or this howto:
[HOWTO: Solving resolution/refresh rate problems in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")

i doubt that since 75 Hz was no problem in windows xp

---

### Post by heimo on 2007-04-17
> **dv5237 said:**
> i doubt that since 75 Hz was no problem in windows xp

Ok.

---

