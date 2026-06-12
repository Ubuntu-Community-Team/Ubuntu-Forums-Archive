---
title: "Printer Settings GUI not appearing"
date: 2019-01-15
forum: General Help
---

### Post by candtalan on 2019-01-15
Hi, a friend's Ubuntu 16.04 has recently failed to run the Settings Printer GUI. The Settings menu icon set seems normal, it shows the Printers icon link, however, when that is clicked, the highlight immediately blinks out and the printer GUI does not appear. (I see that other settings functions icon remain showing selected while they briefly run up). No Printer GUI appears. The printer has now been unplugged and the laptop restarted, - no change. I ran [http://localhost:631/admin](http://localhost:631/admin)  and although I am unfamiliar with that approach, it lists the printer as disconnected, which is currently correct, and it all looks sort of sensible. 
I have also done  sudo apt-get install --reinstall system-config-printer-gnome which seems to reinstall ok, but no change. Comments appreciated tia

---

### Post by him610 on 2019-01-15
Were the appropriate printer drivers installed? Was the printer setup accomplished with the CUPS configuration tool (settings>printers)? 
What make, model of printer? 
How is the printer connected to computer, USB, LAN, Wireless? Have you tried exchanging cables? 
Have there been any thunder & lightning storms lately (I lost a cable modem, router, printer, and computer to one lightning strike several years ago; it came right down the external coax cable)

---

### Post by candtalan on 2019-01-16
Thanks. Drivers ok, it has all been working ok for (years). setup was normal in fact for this model it was pretty well automatic after the printer connection. HP printer HPLIP recent.USB cable. Using [http://localhost:631/admin](http://localhost:631/admin)  it is seen that the printer is recognised  status is shown correctly - idle, disconnected, processing, printing (Printing does work ok), so lots of stuff works - EXCEPT the GUI settings>printer which means that the existing printer cannot be managed (no GUI). The user often needs to manage the print queue, and that is the immediate problem. However it is obvious that a fault exists, guessing thus far in the Ubuntu instance??

---

### Post by him610 on 2019-01-16
>  status is shown correctly - idle, disconnected
***Disconnected ***literally means the printer is not connected to the computer.

---

