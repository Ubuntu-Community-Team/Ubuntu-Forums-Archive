---
title: "recurring printer"
date: 2022-08-12
forum: General Help
---

### Post by angel mike on 2022-08-12
Using Ubuntu 22.04 and have downloaded the Printer from Brother which works but a generic printer keeps coming back after deleting it.

---

### Post by TheFu on 2022-08-12
> **angel mike said:**
> Using Ubuntu 22.04 and have downloaded the Printer from Brother which works but a generic printer keeps coming back after deleting it.

If you print to the "generic" choice, what happens?  It might just be a ghostscript text-only filter.

---

### Post by angel mike on 2022-08-13
Thanks TheFu - it does print and also works for any wifi connected device like my mobile. So perhaps I need not bother downloading the one from Brother Printers even though it has the correct drivers and uses cups ?

---

### Post by mIk3_08 on 2022-08-13
> **angel mike said:**
> Using Ubuntu 22.04 and have downloaded the Printer from Brother which works but a generic printer keeps coming back after deleting it.
If the generic printer did not cause anything to not be able to print/work your original printer, then just leave it all behind as long as your printer works fine. Maybe you should restart and delete the object or vice versa delete then restart or just kindly checked what processes in your system monitor that allows it to return back when you already remove it. Hope it helps. Regards and cheers.

---

### Post by TheFu on 2022-08-13
> **angel mike said:**
> Thanks TheFu - it does print and also works for any wifi connected device like my mobile. So perhaps I need not bother downloading the one from Brother Printers even though it has the correct drivers and uses cups ?

If it works in the way you like with out the proprietary drivers, great.  Many newer printers follow a "driverless printing" method using IPP, so that no drivers need to be loaded on the systems.  However, I expect some seldom used features or monitoring of consumables may not work ... along with some tracking that all proprietary code has these days.  

If I had a network printer, which I don't, mine are all USB connected, then I'd be certain to block the IP address for the printer from any internet access at all, always, in the router. For network printing, I use CUPS, which has been around for Unix about 25 yrs and is maintained by Apple, as one of the few F/LOSS projects where they actually give back to the community their entire business is built around.

You can learn more about "driverless printing" by googling those terms. It has been around for 10-15 yrs time, but only became popular the last 5, I'd guess.  My next printers will all work driverless and without any computer needed for scanning and faxing. I still use the fax on the brother to deal with the govt.  Last thing I need is for the govt to know any of my email addresses or voice phone numbers. They never attempt to fax either, so it is good, 1-way, communications with them responding via snailmail.  Just 1 less thing to worry about being phished over in my small business.

As for deleting any printers. I wouldn't bother. I'd just set a name that I know and make that the default printer, then be done.  For example, I have a Samsung ML1740 ... which I've named "laser". Simple, to the point, easy to remember.  I have a brother all-in-one which is named "inkjet" which is never used. Laser printing is about 50x cheaper than inkjets, I'd guess. Toner doesn't dry up every year either, needing $25 replacement ink.  I've had the same toner in the laser for, perhaps a decade now. It is starting to run out, so I shake it yearly to redistribute the toner, so light printing areas aren't light anymore.

---

### Post by angel mike on 2022-08-14
Thanks all and for the dissertation on printing - I'll mark this thread as solved. Great stuff.

---

