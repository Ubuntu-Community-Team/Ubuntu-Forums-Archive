---
title: "cups, lpd, ppd trouble install brother MFC-5440cn"
date: 2007-05-20
forum: General Help
---

### Post by volkswagner on 2007-05-20
I am having trouble printing to network printer.  I installed the two packages from brother, lpd and cups wrapper.  I now see the printer and says it is ready but i cant print.  here is an image of my terminal after installing the cupswrapper.

[ATTACH]33045[/ATTACH]

UBUNTU ROCKS

---

### Post by mbradlcu on 2007-05-21
can you find the .ppd file and manually copy it to (I'm guessing here) /usr/share/cups/model/ ?

---

### Post by volkswagner on 2007-05-21
Ok
working now
I was able to run install and find the ppd file in the correct location

the reason why i thought the printer was not listed in avail printers to add was it was at the bottom of the list (not alphabetical). after adding it it shows up in correct (alpha...) location.  

Thanks for the help.....Next is to get sound card working

---

