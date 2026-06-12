---
title: "hp 1315 driver problems"
date: 2006-10-11
forum: General Help
---

### Post by Magnus150 on 2006-10-11
Hello everyone, I have a hp psc 1315 hooked up to a windows box on the network and I want to be able to print to it from this Ubuntu box. I have set it up and it tries to print, the printer makes noise and the light blinks, but it does not print, it is stuck in the queue on the Windows box. I was wondering if this is a driver problem, as I am just using the suggested driver. Thanks for the help!

---

### Post by Craga_89 on 2007-07-15
Having the exact same problem. Using an inbuilt windows vista driver on windows. It automatically found the driver when i connected it via USB so I didn't have to do anything. I've shared it with the network and i can see it fine with ubuntu and print to it, all that happens however is it sounds like its going to print, but never actually does. Just sits there in the print cue.

Any help would be appreciated!

---

### Post by BruisedQuasar07 on 2007-07-23
> **Magnus150 said:**
> Hello everyone, I have a hp psc 1315 hooked up to a windows box on the network and I want to be able to print to it from this Ubuntu box. I have set it up and it tries to print, the printer makes noise and the light blinks, but it does not print, it is stuck in the queue on the Windows box. I was wondering if this is a driver problem, as I am just using the suggested driver. Thanks for the help!

I have a psc 1315 connected directly to the PC with Ubuntu (USB). I used the CUPS recommended 1310series setup. Everythin works fine, except no matter what I do all print is in light yellow! The manual and driver that HP ships with 1315 all in one printers are labelled 1310 series but the Unbuntu supplied CUPS 1310 series driver certainly does not work. Do any of the CUPS supplied HP PSC drivers at least work well enough to give us black ink print? 

--Bruised

---

### Post by aparigraha on 2007-08-14
You might wanna have a look at this:

[https://help.ubuntu.com/community/HpAllInOne]("https://help.ubuntu.com/community/HpAllInOne")

I had the exact same problem with my HP PSC 1215
It printed only black and the color yellow. I solved it by installing sane, libsane, sane-utils, xsane.

Have a look at this HowTo:
[https://help.ubuntu.com/community/HPPrinterInstallation/PSC1210]("https://help.ubuntu.com/community/HPPrinterInstallation/PSC1210")

It might NOT work on the PSC 1315 models, But this is the ONLY way that i could get color printing to work on a PSC 1215. Everything else failed. I even tried the PSC 1315 HPLIP included in (X)Ubuntu. I was able to print in black an yellow here as well.

You might also want to fiddle around under your Printer settings a bit.
After I installed I changed the Printout Mode to: 600dpi, Color, Black + Color Cartridge
This was the only way to get the printer to actually use both cartridges.

Everything works fine after that.

---

