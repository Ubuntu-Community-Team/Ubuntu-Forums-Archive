---
title: "HP Laserjet Printer won't print until I push the button"
date: 2007-10-17
forum: General Help
---

### Post by Doughy on 2007-10-17
I recently installed  the beta version of Ubuntu 7.10.  I am using an HP laserjet 1350n printer on a network, and every time I try to print a document, the printer's orange light starts blinking.  It will not print the actual document until I go push the button on the actual printer, after which the print is flawless.  I am using the recommended ps driver.

Any ideas on why this is happening?  It was not a problem with ubuntu 7.04.

---

### Post by rbmorse on 2007-10-17
You have the manual feed paper tray selected as default paper source. 

If you have HPLIP installed, start that (system > administration > hplip) then select the printer in the left panel (if you have more than one connected) then click on the "print settings" tab and scroll down until you see "general."   In that panel you will see a setting for paper source.  On my 2605DN the internal tray is tray 2. 

If you don't have HPLIP installed go to system > administration > printing, select your printer in the left panel, then click on the "printer options" tab and select the correct paper tray.

---

### Post by Doughy on 2007-10-18
rbmorse,

That fixed the problem.  Duh!  Thanks so much for your help.

---

