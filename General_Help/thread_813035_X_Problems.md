---
title: "X Problems"
date: 2008-05-30
forum: General Help
---

### Post by newbrain on 2008-05-30
Hi,
   I a real green horn when it comes to linux so please be patient with me. I've just installed ubuntu 8.04 (2.6.24-17) onto my old Dell GX270. I have updated the bios (A07).

When ubuntu is loading i see the progress bar, and everything looks fine. However when it comes to the login-screen. the refresh rate is set to high, and the monitor has problems. when i log it, it reset the refresh rate back (becuase i went into the System/Pref/Screen Resolution and changed it)

My question is this. how do i configure ubuntu to use the correct refesh rate between the progress bar, the unbuntu desktop. I have looked at xorg.config, but it does not seem to contain what I expected:

Section Screen
  Identifier "Default Screen"
  Monitor    "Configured Monitor"
...

what does configured monitor mean, and were is all the resolution and rate stuff I expect to see..

Oh i should point out that the Dell uses the intel exteme2 graphics chipset (nice....)
Section "Screen"

Regards
Steven (NewBrain)

---

