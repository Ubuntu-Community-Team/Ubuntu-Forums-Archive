---
title: "SMB Printing"
date: 2007-08-08
forum: General Help
---

### Post by Greslore on 2007-08-08
I am currently building a Kubuntu 7.04 linux image for a lab environment.  The printers are run off a Windows machine.  The challenge I am working on is trying to get all linux side users who log in to be able to print to our printers without them needed to set it up themselves.

If I install the printer via SYSTEM SETTINGS > PRINTERS > ADD > SMB Shared Printer (Windows) > NORMAL ACCOUNT (I enter in my network ID and password here) > NEXT > (enter in my Windows Domain, Server, Print Queue Name > FINISH  -  It works fine.  However, I would like to avoid having each user logging in to do these same steps.  As the number of users is going to be a fairly large amount for each machine.

Is there a way I can script this at user login somehow?  Maybe in /etc/profile?

---

### Post by Greslore on 2007-08-08
Or is there a way I can set up an SMB Printer via command line?

---

