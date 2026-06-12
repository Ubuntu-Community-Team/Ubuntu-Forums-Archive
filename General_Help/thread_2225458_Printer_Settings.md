---
title: "Printer Settings"
date: 2014-05-21
forum: General Help
---

### Post by mn_voyageur on 2014-05-21
I am running 12.04 LTS.  

How do you view the printer settings for an installed printer?  

I am trying to determine which the IP address is assigned.  I never reserved the IP address, when I purchased a new printer.  All of our laptops were printing.  Now they are not.

I am guessing that someone power cycled the printer and the router assigned a different address.  If I am able to determine the original IP address, I will be able to reserve that address in the router.  

Thanks,
MarkN

---

### Post by deadflowr on 2014-05-21
Is this a network printer?
open a browser and type this
```
localhost:631
```
should give you the cups interface.

Or else look in the program "Printers"
(right click on a listed printer will give a properties option open that to see a particular printers settings)
Or simply try re-adding the printer.

---

### Post by mn_voyageur on 2014-05-21
deadflowr,

Right clicking on the printer did nothing.  

I was able to locate the printer through the "CUPS" Home page.  (Administration tab and then Manage Printers.)  However, I am unable to identify the IP address of the printer.

MarkN

---

### Post by deadflowr on 2014-05-21
perhaps nmap can help.
Install it if not installed
```
sudo apt-get install nmap
```
then try
```
sudo nmap -sP 192.168.1.0/24
```
(if nothing happens try changing the .1. to .0.)
it should list all connected devices.See if you can spot the printer.

---

### Post by mn_voyageur on 2014-06-02
Sorry for the delay.

nmap worked.  I will have to read up on it.

Thanks,
MarkN

---

