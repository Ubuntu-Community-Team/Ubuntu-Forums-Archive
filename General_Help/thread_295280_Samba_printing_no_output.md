---
title: "Samba printing: no output"
date: 2006-11-07
forum: General Help
---

### Post by jeffbarish on 2006-11-07
I thought that I had this problem licked, but I was wrong.  I have gotten my printer to work from Windows XP using Samba three times, but all three times it has spontaneously stopped working after a while.  The last time I managed to get SWAT working also, so I can now see that the print request is in the printer queue, but nothing ever prints.  Windows tells me that the item is printing.  Would it help to see my smb.conf?  The fact that printing has worked suggests that it is set up correctly.  Also, the fact that the print job is in CUPS suggests that Samba is set up correctly.  All three times I got the printer to work I did some fiddling with smb.conf, all of which seemed gratuitous to me, and then tried various combinations of rebooting Windows, rebooting Ubuntu, and deleting/adding the printer in Windows.  Ah, I see now in xtpsetup (TurboPrint setup) that the usb device does not exist again (the device URI is not available under Device name).  If I were to delete the printer, I would not be able to reconnect it.  CUPS, however, is perfectly happy and shows the correct URI.  I tried restarting CUPS several times.  The URI does not appear in xtpsetup.  Any suggestions?  In the meantime, I will try rebooting.

---

### Post by jeffbarish on 2006-11-07
Sure enough, after rebooting the URI is again available in xtpsetup and printing works from Windows.  Clearly the problem is on the Linux side.  It seems to have something to do with the device driver for USB.  Yes indeed.  It is related to VMware (which is how I run Windows XP).  When I connect my other printer directly to the VM, the connection to my main printer dies.  Evidently, this is a VMware issue.  I don't suppose anyone out there knows anything about VMware.  I used to be able to connect the main printer to the Linux machine and the label printer directly to the VM (before I upgraded to Edgy).  I suppose I'm going to have to figure out how to use the Dymo LabelWriter with CUPS (it's not supported).

---

### Post by jeffbarish on 2006-11-08
Apparently the Dymo LabelWriter *is* now supported in CUPS.  I used the browser interface to add a printer.  I put an entry in smb.conf and restarted Samba.  I added a printer in XP.  It worked!  The next time I'm raising welts from banging my head on some frustrating problem, remind me that there was a time when something just worked.

---

