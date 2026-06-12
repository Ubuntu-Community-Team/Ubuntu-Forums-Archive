---
title: "priting from dosemu to CUPS"
date: 2014-01-20
forum: General Help
---

### Post by ray_field2 on 2014-01-20
for ten years I printed happily to an HP 1300 laser printer, which alas became unusable. yesterday I replaced it with a LaserJet P1102w, which works fine in LibreOffice, Firefox, etc. 

however, it will not print from dosemu, although it's set as the default printer. the 1300 handled this just fine out of the box, but now when I issue a print command from the DOS application, the print status box acknowledges receipt (from "unknown(stdin)"), but closes without printing after the 20-second timeout.

I can print the document with lp [filename], though it comes out unformatted.

a post I saw suggested editing /usr/share/cups/mime/mime.types to add the rules for text/plain to application/octet-stream. since the mime.types file warned me not to change it, I created a new "local.types" file containing

```
#
########################################################################
#
# Raw print file support...
#
# Comment the following type to prevent raw file printing.
#

application/octet-stream            txt printable(0,1024)

#
#
```

still no joy. am I getting warmer?

---

### Post by ray_field2 on 2014-01-20
just to clean this up: further research unveiled that this P1102w relies on the host for most processing -- I guess what we used to call a "win" printer. there was some evidence updating the firmware would make it possible to render plain-text the way that HP PCL used to, since for one thing the latest f/w allows for HP's e-printing with phones and tablets. 

but after updating the firmware, I still couldn't get it to take. so I'm just using the old app's PS printer to create a PDF and printing that. by no means a dealbreaker, but if anyone finds otherwise, please leave a note!

---

