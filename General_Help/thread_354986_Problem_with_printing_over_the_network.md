---
title: "Problem with printing over the network"
date: 2007-02-06
forum: General Help
---

### Post by Jango on 2007-02-06
Hello!

I have 3 computers in a network, one has a printer hooked up (that computer is running ubuntu). The other one is on windows and uses http:// port to print and it works fine. 

The second laptop has Ubuntu... I tried to make it printing... but  all what i get is 

-12345X@PJL ENTER LANGUAGE=PCL3GUI
17H1-1M126Ao0M1-2Hg20WXX XX
u600Dr4812Sr1AP58Yb0Vb23W]

for anything that is printed from that laptop.

Can anyone help me?
Thanks a lot, Nikita

---

### Post by Jango on 2007-02-07
NVM, I guess I found the solution :)

---

### Post by n0ah on 2007-03-15
> **Jango said:**
> NVM, I guess I found the solution :)

Could you post the solution then please?

---

### Post by Jango on 2007-05-10
try this page: [https://launchpad.net/ubuntu/+source/cupsys/+bug/55828](https://launchpad.net/ubuntu/+source/cupsys/+bug/55828)

I used that adbive by Pascal De Vuyst at 2006-08-15 12:02:46 UTC

"Forget about the workaround I mentioned before by setting up a raw queue on the server.

When setting up an IPP printer with gnome-cups-manager on a print client you always have to associate a PPD with it by selecting the manufacturer, model and driver for your printer.
This doesn't make sense for a network printer, since you have already configured the manufacturer, model and driver on the print server.

To make it work you can setup your printer manually with the following command:
$ lpadmin -p printername -E -v ipp://10.0.0.40/printers/dj3820

Another possibilty is to activate browsing on the server to let your print client autodetect the printers.
You can easily enable browsing on an Ubuntu print server by running the following command:
$ sudo /usr/share/cups/enable_browsing 1
Then start gnome-cups-manager on the print client an activate Global settings > Detect LAN printers. Now wait 30 seconds and your printers will appear.

In both cases you will see that the "Paper" and "Advanced" tabs are disabled in the "Properties" of you printer in gnome-cups-manager, this is normal.

Associating a PPD with an IPP printer with gnome-cups-manager worked in CUPS 1.2.0 and 1.2.1, this behaviour seems to have changed in CUPS 1.2.2.
This could be a bug in CUPS 1.2.2, but IMHO setting up an IPP printer associated with a PPD file doesn't make sense since you already configured the printer on the server. Therefore gnome-cups-manager should be altered so it doesn't ask the manufacturer, model and driver for an IPP printer.
Also printing options should be visibile in the "Paper" and "Advanced" tab of the printer "Properties". These options should be read from the server which is perfectly possible now from the following command line:
$ lpoptions -d printername -l
These printer options are set on the server but gnome-cups-manager should allow for an override on the client in ~/.cups/lpoptions."

I used the LAN DETECTION (from the GLOBAL settings menu). It worked just fine,
good luck!

---

