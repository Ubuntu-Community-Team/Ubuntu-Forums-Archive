---
title: "print from osx to ubuntu through the network"
date: 2007-09-16
forum: General Help
---

### Post by Digitallysick on 2007-09-16
How do i print from osx through the network to my hp printer thats connected to my ubuntu box?

---

### Post by JinxAu on 2007-09-16
Gday Digitallysick,

OS X supports printing via CUPS (Common Unix Print System) that is used in Linux as well as OS X. 

Assuming you have got your HP printer working on your Ubuntu box, click on System -> Administration -> Printing. Under the global settings, enable print sharing.

On your Mac OS X box, you will need to add the print queue using the Mac Print manager... there should be an IPP printer option in there somewhere (been a while since I have used OS X). You need to add an IPP printer with the address such as the following:
ipp://<UbuntuBoxIPAddress>/printers/<PrinterNameAsItAppearsInUbuntu

If you want to exact address, on the Ubuntu box, open your web browser and goto [http://localhost:631/printers/](http://localhost:631/printers/) . It should list your installed printers.

Cya round
Jinx

---

