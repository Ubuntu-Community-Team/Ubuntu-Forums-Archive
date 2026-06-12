---
title: "Can't print to printer shared on Windows 10"
date: 2017-12-08
forum: General Help
---

### Post by peyre on 2017-12-08
Our printer is an HP LaserJet P1102w, and my wife leaves her computer on 24/7 (I know, don't get me started)--but since she insists on leaving it on all the time, I set up her computer as our print server.

Now this all worked fine under 2000, XP, and 7, but once we bought her a new Dell that was running Windows 10, I could no longer print to it from my Xubuntu machines.  This has been going on for some time now, through two or three Ubuntu releases.

The printer is shared and all the permissions and everything look right.  In fact I was able to print to it over the network from her Windows 7 laptop, but neither my laptop nor desktop (both running Xubuntu 64-bit) have been able to print to it.  It rejects my credentials, even the ones I used to connect from the Windows laptop. :mad:

I can't seem to find anything online directly addressing this issue.  Can anyone suggest what I might be missing?

---

### Post by Autodave on 2017-12-08
Are  you trying to print via USB cable, ethernet connection, or wirelessly?

---

### Post by SeijiSensei on 2017-12-08
Open a browser on a Linux box and point it to [http://localhost:631/](http://localhost:631/).  That will bring up the CUPS administrative interface.  Choose "Adding Printers and Classes."  See if the software can find the printer on its own with the "Find New Printers" button.  If it does not see it, you'll need to add it manually with the "Add Printer" method.  (Enter your Ubuntu username and password when prompted since the app needs sudo rights.)  Try the "Windows Printer via SAMBA" option first.  If that doesn't help, maybe try the "Internet Printing Protocol" alternative.

I presume you're not running a firewall on the Win10 box since you can print to the device from another Windows machine.

---

### Post by peyre on 2017-12-08
It's connected to her computer via USB.  I'm connecting to it over the network.

---

### Post by SeijiSensei on 2017-12-08
Yes, I realize that.  That's why I suggested the two network-based methods, via SAMBA or IPP.

---

### Post by peyre on 2017-12-08
Sorry, I was replying to Autodave just then.  The troubleshooting you suggest will have to wait until I get home this evening, but I will try it then.

---

### Post by peyre on 2017-12-08
Ok, I tried that.  It's just like before - I'm able to install the printer without error, but when I try to print something, it just sits there in my print queue and apparently never goes to her computer to send to the printer.

---

