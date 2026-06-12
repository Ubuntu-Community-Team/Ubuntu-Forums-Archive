---
title: "Printing with TurboPrint - frustrated!"
date: 2006-11-07
forum: General Help
---

### Post by colinmcd on 2006-11-07
Hello, I am fairly new to linux and have been trying to get my Canon MP130 printer to work.  I have tried using drivers from the canon japan website (for the ip1500) by downloading the rpms, using alien, then installing the debs but it would not work).

I then got this program called "turboprint" which includes a non-native driver for my printer.  Whenever I install the printer and try to print a test page, the lcd on the printer displays "printing" but just hangs until I unplug the printer.  I am getting an error message in the printer properties that says: Printing: No %%BoundingBox: comment in header!


I am SOOO frustrated, please let me know of ANYTHING I could possibly try.

Thanks!

---

### Post by colinmcd on 2006-11-07
I am also getting the following error messages in my CUPS log quite frequently: 

E [07/Nov/2006:01:17:18 -0500] [Job 19] No %%BoundingBox: comment in header!
E [07/Nov/2006:01:17:20 -0500] cupsdAuthorize: Local authentication certificate not found!

---

### Post by wacole on 2006-12-04
Having the same problem w/my Canon S600 with the same error message in the /var/log/cups/error_log file, and have posted to the Turboprint Forum [http://www.turboprint.de/english.html]("http://www.turboprint.de/english.html").  I'll let you know what they say or you can check the forum out.

Good luck.

---

### Post by budgie9 on 2006-12-04
Try using one of the other Canon printer drivers in the listings.
For me with my i860 I think it was the BJC7000 and 4000 drivers that worked great. One for text and the other for graphics printing.

I also downloaded the printer drivers from Japan. I changed those to deb files and installed them. 
I found I had to install them in a specific order else they failed to work. 

If I recall correctly, the Common file, ONLY the 2004 version, was installed first, the 2006 version does not work for me, followed by the lib files - libtiff3g, libpng2005, then the Pixus, and the Cups file. 

If the lib files are not loaded or the Common2006 version are used then the printer drivers will not work.

I tried Turboprint though I suspect that Turboprint simply redirected my printer to those drivers mentioned anyway. At least it printed exactly the same as with those drivers. So I never bought the program.
If no luck wiith the above, you may find one of the listed drivers will at least get you printing until a driver appears for your printers.

Hope this helps.

---

### Post by wacole on 2006-12-04
Just to let you know that in poking around on some other forums I found that someone else w/a Canon had installed the 1.94-3 (now 1.94-4) version of Turboprint which solved his problem.  So, I installed the current Turboprint, 1.94-4 and all is well!

Hope this works for you.

---

