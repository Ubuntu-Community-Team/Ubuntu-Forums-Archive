---
title: "[AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470] ?"
date: 2015-03-13
forum: General Help
---

### Post by pirate3 on 2015-03-13
hello guys

am new on ubuntu and my question is my pc built up with [[COLOR=#008000]**AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470**[/COLOR]], but when open system setting and click on detail icon that can show me this video card i just see this Gallium 0.4 on AMD RV620, instead of my original driver (AMD/ATI), and because of that i think my video performance is kind bad that even  i cant play any game that i just used to play before when i was using windows 7, please guys help me any suggestion  for this because i real like try using ubuntu os thank.

OS that running this laptop is **[COLOR=#006400]UBUNTU 12.04 LTS [/COLOR]**

---

### Post by mastablasta on 2015-03-13
the chip is no longer supported by AMD so what you have there are opensource drivers.  system gives correct information. 
opensoruce driver: Gallium  
AMD chip number: RV620

still the opensource drivers for this card should offer reasonably good support. but they are far from perfect on some cards (far from windows performance at least).

for windows games windows is still the best.

what are your specific issues? can you maybe run some benchmarks? maybe run phoronix suite some unigine benchmark or maybe glmark2 (both in repositories)

since you have mobility version I wonder if RAM is propperly assigned to the chip. also it might be using more CPU in linux

---

### Post by mörgæs on 2015-03-13
Open source AMD drivers have improved a lot and I recommend at least kernel 3.16.

---

### Post by grahammechanical on 2015-03-13
I have an Nivida card and when I use the open source video driver I see that message about Gallium 0.4 but when I use the Nvidia proprietary driver I see Geforce GT 220/PCIe/SSE2. The details page is giving us a simple way of knowing if we are running on the open source driver or the propriety video driver. If we see llvmpipe then that means that there has been a conflict with the proprietary video driver and we are now running on an open source fall back video driver. 

You could try using Additiional Drivers to set a proprietary video driver. Make a note of the version numbers of the drivers available. If those drivers do not have support for that video card then use Software Centre to find an older driver, a legacy driver. But please keep this in mind: If you upgrade From 12.04 to 14.04 you will get the latest stable proprietary video drivers. Newer versions to the ones now available to you and if those drivers no longer support that video card there will be problems when you re-start. So, before upgrading to the next version of Ubuntu revert to using the open source video driver.

One more thing we can often use Recovery mode>Resume to load to a desktop using llvmpipe when things go wrong with video drivers.

Regards.

---

### Post by pirate3 on 2015-03-13
much appreciate all of you

---

