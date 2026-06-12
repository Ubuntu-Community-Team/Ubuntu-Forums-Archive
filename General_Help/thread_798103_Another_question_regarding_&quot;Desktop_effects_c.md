---
title: "Another question regarding &quot;Desktop effects could not be enabled&quot;"
date: 2008-05-17
forum: General Help
---

### Post by tcity5 on 2008-05-17
I realize that there are infinite topics about this question, so let me explain what I know.  I go to System>Preferences>Appearance>Visual Effects.  When I try to set it as normal or extra, I get the error saying "Desktop effects could not be enabled".

I do not know what type of graphics card I have, but it is integrated.  I put the computer together with spare parts I collected, except for the 1GB DDR PC3200 RAM I bought for it.

I upgraded to the new 8.04LTS version of Ubuntu to try to fix the problem, but I had no luck.  I tried System>Administration>Hardware Drivers, but it says that "No proprietary drivers are in use on this system."

---

### Post by overdrank on 2008-05-17
> **tcity5 said:**
> I realize that there are infinite topics about this question, so let me explain what I know.  I go to System>Preferences>Appearance>Visual Effects.  When I try to set it as normal or extra, I get the error saying "Desktop effects could not be enabled".

I do not know what type of graphics card I have, but it is integrated.  I put the computer together with spare parts I collected, except for the 1GB DDR PC3200 RAM I bought for it.

I upgraded to the new 8.04LTS version of Ubuntu to try to fix the problem, but I had no luck.  I tried System>Administration>Hardware Drivers, but it says that "No proprietary drivers are in use on this system."

You can find the graphics  with the command lspci in the terminal and look for VGA.

---

