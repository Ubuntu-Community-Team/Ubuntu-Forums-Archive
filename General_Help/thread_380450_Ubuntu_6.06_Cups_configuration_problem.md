---
title: "Ubuntu 6.06 Cups configuration problem"
date: 2007-03-09
forum: General Help
---

### Post by Caritas on 2007-03-09
I am a novice Ubuntu user.  I've been able to install U-6.06 and it's working well.  I moved on to installing a printer using cups.  The Ubuntu 6.06 pc is on a home lan with a Hawking HPS12U print server.  All the other pc's on the lan are windows.

The Hawking documentation explains how to install the printer as an IPP printer which  I did.  The printer, a NEC870, has a lan IP address of 192.168.1.200 so the URL in the cups install was [http://192.168.1.200/lpt1:631](http://192.168.1.200/lpt1:631).  Using global settings I opened port 631.  The cups printer install suggested that the driver ljet2p should be used so I installed that.  

All looks good, the NEC870 appears as a printer and is set as the default.

However, when I try to print a test page or try to print any document on the pc the printer almost immediately goes to "pause". That is, with the print queue open, I send a document to print and I see in the queue the :"state" change tp "printing" but then change immediately to "stopped: job stopped".  I try to resume the print but it does not work.  

Any advice on what to do next?

---

### Post by Caritas on 2007-03-09
Since posting my first message above, I've found /var/log/cups/error_log.

Browsing through the error log I found:
[09/Mar/2007:15:54:16 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [09/Mar/2007:15:54:17 -0500] copy_model: empty PPD file!
E [09/Mar/2007:15:54:17 -0500] PID 22056 (/usr/lib/cups/daemon/cups-driverd) stopped with status 1!
E [09/Mar/2007:15:54:17 -0500] [cups-driverd] Unable to open "/usr/share/cups/model/NEC-SuperScript_870-ljet2p.ppd" - No such file or directory
E [09/Mar/2007:15:54:37 -0500] copy_model: empty PPD file!
E [09/Mar/2007:15:54:37 -0500] PID 22084 (/usr/lib/cups/daemon/cups-driverd) stopped with status 1!
E [09/Mar/2007:15:54:37 -0500] [cups-driverd] Unable to open "/usr/share/cups/model/NEC-SuperScript_870-ljet2p.ppd" - No such file or directory
E [09/Mar/2007:15:54:44 -0500] [Job 7] No %%BoundingBox: comment in header!
E [09/Mar/2007:15:54:45 -0500] PID 22091 (/usr/lib/cups/backend/http) stopped with status 2!
E [09/Mar/2007:15:56:43 -0500] Resume-Printer: Unauthorized
E [09/Mar/2007:15:56:44 -0500] PID 22237 (/usr/lib/cups/backend/http) stopped with status 2!
E [09/Mar/2007:15:58:39 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [09/Mar/2007:15:58:45 -0500] cupsdAuthorize: Local authentication certificate not found!

I then successfully copied the ppd file into /usr/share/cups/model/ but the same problem persists.

---

### Post by Caritas on 2007-03-13
Does anyone have any ideas?

---

### Post by Joe King on 2007-03-20
Open up the printer's properties dialog and check that the paper type selected in the "Paper" and "Advanced" tabs matches the paper type loaded in the printer.  This was the cause of a similar problem that had me stumped for a few days when I first started out with Ubuntu.

---

