---
title: "Oracle VM VT-x"
date: 2013-04-06
forum: General Help
---

### Post by Spae on 2013-04-06
> VT-x/AMD-V hardware acceleration has been enabled, but is not operational. Certain guests (e.g. OS/2 and QNX) require this feature.
Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer.
Before it was telling me to enable it in my bios but i ignored it by clicking continue. It warned me again with the above message and after clicking continue again the os sat on an image of 4 blue squares(windows)/failed to start and then goes to a console mode and tells me to restart ( doesn't help ).

I've had this problem before on this same pc, though i forgot what the solution. I don't think it can be to do with the bios settings as they haven't changed since last time.
3570 cpu ivy.


What to do

---

### Post by Cheesemill on 2013-04-06
You need to boot your computer into its BIOS settings and enable VT-x.

The error message you are getting is when you have tried to enable VT-x in your VirtualBox settings but it isn't enabled in your BIOS.

---

