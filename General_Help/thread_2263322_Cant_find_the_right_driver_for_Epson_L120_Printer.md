---
title: "Cant find the right driver for Epson L120 Printer"
date: 2015-01-31
forum: General Help
---

### Post by rodel_catajay on 2015-01-31
bought a new printer,in the selection of the model/maker,under epson, i cant find the model L120,even in the look for online driver, found no match for that model.

what will i do next?

please help.

thanks.

rodel;)

---

### Post by lovelysaint on 2015-05-15
go to CUPS by opening the browser and typing
[http://localhost:631](http://localhost:631)
add printer
EPSON L120 is not found of course, so I used: Driver:Epson Stylus C120 - CUPS+Gutenprint v5.2.9 (color, 2-sided printing)
and it works just fine.
I actually tried so many drivers but this is the only one that matches it.
EPSON L120 does not have a specific driver for Ubuntu...

I hope this helps. 
cheers :)

---

### Post by pdc on 2015-05-18
so looks like gutenprint works but epson DO provide a driver ............. one starts here .............. [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and typing in L120 takes you to here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=28670&DSCCHK=53cfb9ab4d3a2c653ab39ac6a0b590ff64cf0c71](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=28670&DSCCHK=53cfb9ab4d3a2c653ab39ac6a0b590ff64cf0c71)

and for Ubuntu, that runs debian packages the choices are epson-inkjet-printer-201310w_1.0.0-1lsb3.2_i386.deb or epson-inkjet-printer-201310w_1.0.0-1lsb3.2_amd64.deb 

and before installing, Epson remind one to install lsb if it is not already installed;

---

