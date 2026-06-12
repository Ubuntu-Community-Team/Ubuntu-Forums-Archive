---
title: "Foomatic, gimp-print and cups"
date: 2004-10-31
forum: General Help
---

### Post by frspin on 2004-10-31
I am new of Ubuntu and Debian
After installing Ubuntu, foomatic and gimp-print I am no able to define a printer with a foomatic or a gimp-print driver.

Using Computer->System configuration -> Printing and adding a new printer, I get only a cups builtin list of avalaible devices

What I am missing ?

Regards

Franco

---

### Post by adbak on 2004-10-31
You need to enable Universe and then install cupsys-driver-gimpprint and cupsys-driver-gimpprint-data.

---

### Post by frspin on 2004-11-01
I have installed indicated packages bun no change, also after a reboot.
Also. if I add a new printer using lpadmin  I get an error with:

lpadmin: add-printer (set device) failed: client-error-forbidden

What I am missing ?

Regards

Franco

---

### Post by adbak on 2004-11-01
What kind of printer do you have?

---

### Post by frspin on 2004-11-03
I have tried with a parallel printer (Epson stylus color 400) and with a "file" printer.
For this test I have modified cupsd.conf file enabling FileDevice.

I have also some network print connected to a server box, running RH9 under CUPS.
This printers work ok also from Ubuntu. My problem is defining "local" printers.

Regards

Franco Spinelli

---

### Post by Joeb on 2004-11-03
[QUOTE=frspin]I have tried with a parallel printer (Epson stylus color 400) and with a "file" printer.
For this test I have modified cupsd.conf file enabling FileDevice.

I have also some network print connected to a server box, running RH9 under CUPS.
This printers work ok also from Ubuntu. My problem is defining "local" printers.

Regards

Franco Spinelli[/QUOTE]


Is your parallel port functioning (ie are the drivers loaded)?  Particularly parport_pc?  You can find out by doing an lsmod and see if it's listed or just try modprobe parport_pc and see if you can then set up the printer (you may have to stop and restart cupsd, first).

---

### Post by frspin on 2004-11-04
From lsmod I get that parport and parport_pc is running.

Any command as:

sudo lpadmin -p printer -d parallel:/dev/plp 

or

sudo lpadmin -p printer -d file:/tmp/file.tmp

give me same error:

lpadmin: add-printer (set device) failed: client-error-forbidden

Regards

Franco Spinelli

---

