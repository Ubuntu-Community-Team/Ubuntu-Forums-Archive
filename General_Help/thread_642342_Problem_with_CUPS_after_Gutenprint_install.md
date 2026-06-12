---
title: "Problem with CUPS after Gutenprint install"
date: 2007-12-16
forum: General Help
---

### Post by tospo on 2007-12-16
Hi,

I am trying to install my Canon S750 on FeistyFawn using CUPS version 1.2.8
I followed the instructions I found for this printer in the OpenPrinting database:  [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S750]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S750")
and installed the gutenprint 5.0.1  package (after converting the rpm to a debian package with alien). 

I had previously installed this printer in CUPS as Canon PRIXMA IP3100 because I was told that that would work and it does to some extent but I was hoping to get a better driver by installing gutenprint. Anyway, I deleted the PRIXMA version of my printer and re-installed in CUPS, this time selecting the S800 as recommended on the OpenPrinting database page. The printer was installed but when I try to print the test page the job is stopped although the printer is reported as being idle and ready.
I checked the CUPS error log and there are "status 22" errors, but I don't know what this means. 
Now even when I delete that printer and reinstall as PRIXMA IP3100 as I had done before, I get the same problem and error message.
It looks like I messed up CUPS - how can I reinstall CUPS without breaking anything else or is there a way of fixing my installation?

Thanks for your help!

---

