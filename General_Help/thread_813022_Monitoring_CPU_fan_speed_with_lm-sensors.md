---
title: "Monitoring CPU fan speed with lm-sensors"
date: 2008-05-30
forum: General Help
---

### Post by GammaPoint on 2008-05-30
Hi, I just installed lm-sensors for the first time and am able to monitor my CPU temperatures but it says my fan speed is 0 rpm (*and I'm pretty damn sure that's not true----especially with core temps <10 degrees C*).

Has anyone else had this problem or know what the solution might be?  Thanks for the help.

---

### Post by Titan8990 on 2008-05-30
If your fan is plugged directly into a power connector and not the MOBO it will not be able to read fan speed.

I do not have any experience with Linux versions of hardware monitors but I know in Winodows you may have to try a couple different apps to find one that is compatable with your BIOS. A temperature of 10C indicates that things are probably not being sensed properly unless you are using watercooling.

Hope that helps.

---

### Post by GammaPoint on 2008-05-30
> **Titan8990 said:**
> If your fan is plugged directly into a power connector and not the MOBO it will not be able to read fan speed.

I do not have any experience with Linux versions of hardware monitors but I know in Winodows you may have to try a couple different apps to find one that is compatable with your BIOS. A temperature of 10C indicates that things are probably not being sensed properly unless you are using watercooling.

Hope that helps.

My fan is plugged into my mobo.  I just rebooted my computer and went into my bios setup (where I can also monitor these things) and my CPU temps were more like 21 degrees C and my fan speed was also at ~2500 rpm.  My CPU fan is a bit loud, which my fiancee HATES. Is there a safe way for me to reduce this fan speed? 21 degrees is damn cool already eh?

---

### Post by Titan8990 on 2008-05-30
Is the plug on the MOBO 4pins or 3?

I ask this because the 4th pin is used for speed control.

---

### Post by GammaPoint on 2008-05-30
Yeah, it's got 4 pins so I'm guessing it should be controllable.

---

