---
title: "printing doesn't work - CUPS"
date: 2008-05-21
forum: General Help
---

### Post by aaronp on 2008-05-21
Hi,

Since upgrading to HH8.04 I am unable to print.
I press print, it appears to send the item to my printer (Canon IP3300 on USB using CUPS) and then in the jobs list it says it was a successfully completed job but the printer does absolutely nothing.

Any ideas?

thanks
Aaron

---

### Post by mrprefect on 2008-05-21
Did you try removing and re-adding your printer?

May also want to do a tail on your cups log files /var/log/cups and see if says anything isn't working

Might also want to restart cups and see if it spits out any errors

/etc/init.d/cups restart

---

### Post by jdbernard on 2008-06-06
I am going to bump this thread, b/c I have had the exact same problem but with a different printer.

I am having the same problem with an HP OfficeJet J3680 All in One printer.

Under 7.10, I had a similar problem that turned out to be a permissions problem regarding the /dev/bus/usb device that the printer was on. The fix was to make this device world readable.

This was broken when I upgraded to 8.04

The HPLIP site shows this pinter as fully supported, and it is detected and auto-configured when I plug it in. It just doesn't print, though it says Job Finished, like the original poster.

I have tried deleting and re-installing the printer through the gnome tools, hp-toolbox, and the CUPS settings, all to no avail. I have tried all the HP drivers that sound remotely close to the model number (HP OfficeJet J5700 Foomatic/hpijs, hpijs 2.8.2 is the 'correct' driver for this printer). I have tried stopping, starting, restarting the CUPS print sever. I've scoured the error-log file for anything that could lead to the case, but the only thing I can tell is an error is stuff similar to 'cupsdSendError: 14 code=304 (Not Modified)' Googleing for information on this error code turns up nothing.

Any help would be appreciated. I've exhausted the amount of time I'm willing to work on this. It seems this problem may not be specific to this printer only.

Attached is the log from /var/logs/cups/error-log (set to log Debug level, of course).

---

### Post by aaronp on 2008-06-06
FYI mine was resolved when I completely re-installed the printer from the Canon drivers.

Good luck with yours.

---

### Post by jdbernard on 2008-06-06
Thanks, aaronp. 

Unfortunately  for me, I don't think HP makes drivers for Linux. Anybody have a PPD for something close to a J3680?

---

### Post by aaronp on 2008-06-06
Sounds like nothing to do with your drivers so this is a long shot, and you may have already gone through this but here goes any way:

[http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_J3600](http://openprinting.org/show_printer.cgi?recnum=HP-OfficeJet_J3600)

hope it helps.
Aaron

---

### Post by fheinsen on 2008-09-22
Downloading and installing the driver from openprinting.org worked for me on Ubuntu 8.04 (the default driver never worked).  The driver can be downloaded directly from here: 

[http://openprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-OfficeJet_J3600&show=0](http://openprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-OfficeJet_J3600&show=0)

---

