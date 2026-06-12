---
title: "Uninstalling Corrupted Printer"
date: 2007-01-30
forum: General Help
---

### Post by JustDon on 2007-01-30
I have a printer installed as a "Windows SMB Printer", named KONICAMI for Konica Minolta. It is a laser printer connected to a Windows XP machine in my network. It has always worked perfectly with my dual booted machine. We moved our home office into a store front office location and the KONICAMI is now connected to the same Windows XP machine except on a USB port instead of LPT1 port. Now, I cannot print to it. I installed "new printer" and now have the exact same printer on the exact same XP machine that is now named KONICAMI - 1. It works great. My question involves getting rid of the non-functioning KONICAMI that appears to be corrupted. It always says "paused". Any ideas on getting this uninstalled/deleted?

---

### Post by kebes on 2007-01-30
In a web-browser, go to the CUPS admin page:
[http://localhost:631/](http://localhost:631/)

Select the tab "printer" and then "delete printer".

You can also click "cancel all jobs" and "stop printer" before deleting it, just to be sure. You can also use this page to rename, modify, or otherwise manage the new printer connection, that is working.


Hope that helps.

---

