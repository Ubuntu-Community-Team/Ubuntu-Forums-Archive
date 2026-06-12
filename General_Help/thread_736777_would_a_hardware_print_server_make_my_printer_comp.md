---
title: "would a hardware print server make my printer compatable?"
date: 2008-03-27
forum: General Help
---

### Post by android6011 on 2008-03-27
My printer isnt compatable with Ubuntu or linux at all and I've wanted to get a print server so I can put my printer in the room with my router anyway, so my question is will hooking up my printer to a print station make it compatable with ubuntu or will ubuntu still require some sort of driver? thanks

---

### Post by luceerose on 2008-03-27
You have tried the Gutenprint drivers, haven't you ???

If not, find it with Synaptic and install it before you do anything else.
Gutenprint and everything it needs to operate consist of these 5 packages;

cupsys-driver-gutenprint
foomatic-db-gutenprint
ijsgutenprint
libgutenprint2
libgutenprintui2-1

If all 5 are not already installed, install what's missing & reboot.

EDIT: I forgot >>>    hal-cups-utils
Some printers identify themselves with a HAL id & need this package to communicate with the PC.
Install that along with the other 5.

---

