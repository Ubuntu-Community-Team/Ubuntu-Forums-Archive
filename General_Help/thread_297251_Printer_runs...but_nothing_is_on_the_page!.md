---
title: "Printer runs...but nothing is on the page!"
date: 2006-11-10
forum: General Help
---

### Post by AceRimmer on 2006-11-10
Hello.  I have an HP Deskjet 825C connected and Edgy sees it.  I send a document to it and it starts up and the printer acts like it is printing...but nothing is put on the paper!  I tried it in Windows and it printed a test page without a problem.  Help!

---

### Post by AceRimmer on 2006-11-16
No ideas on this one?

---

### Post by s_h_a_d_o_w_s on 2006-11-16
Sorry to be ovious, but lets rule out physical failure. It has ink, right?

---

### Post by fragos on 2006-11-16
Define Edgy sees it.  lsusb or System-> Administration-> Printing.

---

### Post by AceRimmer on 2006-11-25
It has ink since I can print to it when I boot into WinXP, in the PRINTERS section I see the printer and it shows the printer and I have the driver selected that it recommends, the one that matches the name of my printer.  I'll try some other drivers maybe.  I tried the "Hight Quality Image (Gutenprint)" driver and it prints, but the printer sounds weird when doing it and doesn't print out text in the normal quality, it is a bit fuzzy instead.

---

### Post by fragos on 2006-11-25
HPLIP drivers are supplied by HP and have always worked well for me with a variety of HP printers.  Ubuntu comes with a current version of HPLIP.  I'm however unfamiliar with your particular printer.  I'm still curious of how you determined Linux sees the printer.

---

### Post by AceRimmer on 2006-11-25
> **fragos said:**
> HPLIP drivers are supplied by HP and have always worked well for me with a variety of HP printers.  Ubuntu comes with a current version of HPLIP.  I'm however unfamiliar with your particular printer.  I'm still curious of how you determined Linux sees the printer.

I go to System->Administration->Printing

It shows 2 icons, "Add New Printer" and "Deskjet 825c" and the deskjet icon has "Ready" under it.

And I did this
> aaron@Cthulhu:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:00d1 Microsoft Corp. 
Bus 002 Device 003: ID 045e:000b Microsoft Corp. Natural Keyboard Elite
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:0704 Hewlett-Packard DeskJet 825c
Bus 001 Device 001: ID 0000:0000

---

### Post by fragos on 2006-11-25
Lsusb shows that Linux can see your printer.  Ubuntu has a configuration for your printer.  Right click the printer icon and select properties to review the configuration.  In the driver tab make sure the manufacturer is set to HP and the model to "Deskjet 825C".  The driver should say hpijs (recommended).  That's the only option you should have.  There is an Install Driver button that would allow you to install additional PPD files which in this case aren't required.  The connection tab should have Local Printer checked.  Mine also has Use a detected printer checked.  Your 825C should be the only one in the list.  You could try to "Print a Test Page".  That should work.  If not we can try to print from the command line.  That may provide an error message that doesn't show up in the GUI.

---

### Post by AceRimmer on 2006-11-28
Thanks for the replies!

I have selected the Deskjet 825C hpijs driver, which is the one that gives me no output.  ](*,)

---

### Post by suterb42 on 2007-06-15
I had this problem, too, until I installed a package called foomatic-db-gutenprint. I'm using the "High Quality Image (Gutenprint Cups) (simple)" driver without any problems.

---

