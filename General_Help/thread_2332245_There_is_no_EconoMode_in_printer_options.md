---
title: "There is no EconoMode in printer options"
date: 2016-07-29
forum: General Help
---

### Post by Daniyal_Javani on 2016-07-29
I check the [EconoMode]("http://h20564.www2.hp.com/hpsc/doc/public/display?docId=emr_na-c00763650") and it works in Windows but there is no option in [http://localhost:631](http://localhost:631) or printer properties. However there are another options like printing quality (Normal/Draft) or print density (Light/Dark) that seems do similar work (But not exacltly). So is there any way to add EconoMode option?
  I also try hplip and adding EconoMode to Other Options (Advanced).
  I'm using Ubuntu 16.04 and laserjet p1102 printer.

---

### Post by DuckHook on 2016-07-29
*Thread moved to **General Help** as the more appropriate forum.*

It is only to be expected that device drivers written for different OSes will behave differently. I don't know your printer model or how "Economode" behaves in Windows, but in Linux, the equivalent would be Draft mode. On my hplip management panel there is no option called "Economode".

> **Daniyal_Javani said:**
> …I also try hplip and adding EconoMode to Other Options (Advanced).

What do you actually mean by this? I don't think you can just add a mode to the printer by filling in an options box with the word, "EconoMode" (if that is what you did). I highly doubt that the driver works that way. It will usually require a command string that looks arcane and with which I am not familiar.

In any case, what is the difference between "Draft" and "EconoMode"?

---

### Post by Daniyal_Javani on 2016-07-29
> **DuckHook said:**
>  what is the difference between "Draft" and "EconoMode"? 
The printed text in EconoMode is slightly lighter, but in Draft mode is very lighter as it's hard to read on small fonts.
 Thanks for your attention

---

### Post by DuckHook on 2016-07-30
> **Daniyal_Javani said:**
> The printed text in EconoMode is slightly lighter, but in Draft mode is very lighter as it's hard to read on small fonts…I doubt that you will get any better result. As far as I know (and I stress that I could be wrong on this) such toner-saving is a function of the driver. Therefore, the way the Linux driver is written is what determines the lightness of this output. I suppose that, if the driver is open source, you could change the parameters and recompile the driver, but that would involve a level of reprogramming that is far outside of my knowledge level. If the driver involves binary blobs from HP, then even such reprogramming my not be possible.

---

