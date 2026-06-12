---
title: "Printing Clips (right and bottom)"
date: 2007-11-04
forum: General Help
---

### Post by RobNY on 2007-11-04
I've been having problems with incorrect print areas and clipping for sometime now.  I'm current runny Feisty (fully updated).  My current printer is an HP Deskjet 6988 configured as a network printer.

The problem is, most everything I print (including Test Pages) clips on the right and bottom.  I have already done the following:

1. Updated PPD file and restarted cupsys
2. Run hp-toolset (after installing all the python/qt dependencies) and checked all settings.
3. Run the "alignmargins" script from linuxprinting.org (the instructions on which are absolutely incomprehensible)
4. Run the "sudo foomatic-cleanupdrivers"
5. Made sure my paper size was set to letter in all the right places including /etc/papersize, the printer config dialog, etc.

I can get Firefox to work by tweaking the settings under Print->properties,  but all other output runeth over...

The printer is configured to use the hpijs driver (current from the repos).

LinuxPrinting.org show this printer to "work perfectly" yet it doesn't for me -- and I'm using their PPD.

Can someone shed some light on what else I might try?

Thanks.

---

