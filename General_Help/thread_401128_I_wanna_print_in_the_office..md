---
title: "I wanna print in the office."
date: 2007-04-04
forum: General Help
---

### Post by kroiz on 2007-04-04
I am at the office and there is a printer (HP LaserJet 4000) connected to the LAN.
System->Administration->Printing
open a error dialog: "The CUPS server could not be contacted".
Please help.

---

### Post by djf_jeff on 2007-04-04
Just type in a terminal :

sudo /etc/init.d/cupsys start

and retry opening the dialog. If it work, just go to System->Administration->Services and activate Printing services.

---

### Post by kroiz on 2007-04-04
thanks after I started the service it starts.
in the Services dialog there is two:
Printer Service: (cupsys)
and 
Printer Service (hplip)

since the network printer is HP should I start the second?

---

### Post by djf_jeff on 2007-04-04
I don't know, here, the two is enabled by default. Maybe to make think easy, start the two, configure everything and when it work, disable it to see if it continue to work.

---

### Post by kroiz on 2007-04-04
I turned them both on and reboot.
but when I try to print, nothing comes out.
I now got an printer icon in the top panel (gnome) which opens a dialog with the list of pending prints. but they are all pending.
When I added the printer I had several options for the driver I chose postscript (it was recomanded) maybe I should choose something else there? but I dont know what.

---

### Post by kroiz on 2007-04-04
Ok I figured it out.
when I add a new printer I use HP JetDirect instead of CUPS and it works.
thanks djf_jeff

---

### Post by djf_jeff on 2007-04-04
Happy to know it work fine for you! Good that you post the solution here for others. Thank you.

---

