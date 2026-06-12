---
title: "Network print server"
date: 2007-11-28
forum: General Help
---

### Post by mb125 on 2007-11-28
I have been trying to set up a mini network printer hooked into my network with no such luck.
Here is all my info
airlink mfp print server connected to my router via ethernet and given a static address of 192.168.0.254 and attached to a HP deskjet 845c by a USB cable.
Ubuntu 7.10 gutsy OS
I have tried every setting in the CUPS interface ipp://192.168.0.254   socket://192.168.0.254:9100  and so on and so on with various HP drivers
i can ping the mini print server and also access its web interface
I cant get it to print out to save my life all i get it host id busy will retry in 5 seconds.
What am i doing wrong??????

---

### Post by mpierce on 2007-11-29
I had a similar problem with an HP Colour LaserJet 2550l.
I finally resolved it (same type of setup as yours) by opening up KControl and setting up the printer there by using the admin privileges at the bottom of the screen.

As I have the samba packages installed, it used the samba protocol.

Hope this helps

---

### Post by gkestrel on 2007-11-29
This is how i added my netork printer in my system.  First i setup my print server and gave it an ip address.  Next i added the printer attached to the print server, Go to System, Administration, Printing.  Click New Printer  Choose Network printer, choose TCP/socket HP JetDirect, raw connection.
Host: add the IP address of the print server , Port: 9100, Click Forward and go on with the printer wizard to select brand, model, install your driver, add settings as you would do for a local printer.  Hope this helps you.

---

### Post by mb125 on 2007-11-29
All i get after i do all that is Network host '192.168.0.254' is busy; will retry in 20 seconds...

---

### Post by mb125 on 2007-12-08
Aparently the Airlink101 mini network printer i have only works with winblows and  after you install there software to communicate with it.

---

