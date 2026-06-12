---
title: "Feisty not working withNvidia card"
date: 2007-04-22
forum: General Help
---

### Post by Arun985 on 2007-04-22
Hi, I have a nVidia GeForce 6200, and when I try to boot Ubuntu Feisty with it, my system just hangs on the loading screen. I should have the latest nVidia drivers already installed, cuz I upgraded from Edgy, and before the upgrade everything was working fine. Can anybody out there help me with this lil problem?

Oh, and Beryl just stopped working recently. I can access the Beryl Manager, but when I try to switch my window manager to Beryl, it stays on Metacity. 

I'd really appreciate some help w/ my problems.

---

### Post by ionophore on 2007-04-22
Why don't you go over to /var/log/ and look at the log files from X.  On my system there is a Xorg.0.log.  I'm not sure what the "0" signifys.  Look for the most recent one and see if there are any lines that begin with (EE) or (WW) and post them here.

---

### Post by nei3k on 2007-04-22
Try this:
System > Administration > Restricted Drivers Manager and see if it's enabled

Worked for me

---

