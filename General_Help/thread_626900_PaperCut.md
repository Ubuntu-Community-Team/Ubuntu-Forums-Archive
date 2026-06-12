---
title: "PaperCut"
date: 2007-11-29
forum: General Help
---

### Post by DGWIRED on 2007-11-29
I am relatively new to linux.  I have setup a box with Ubuntu to act as a file and print server for my home network.  I need to have a print accounting package setup so that I can monitor and split the cost of ink with the other users on my network.  I found an application called Papercut that offers what I am looking for but I am having some issues getting it to work correctly.  The problem I a, running into is that the application requires that  when using CUPS the Device URI on each printer should be modified so the papercut backend is incorporated into the print process by modifying the printers.conf by putting "papercut:" in front of the Device URI like "papercut:hp:/usb/PSC_750?serial=MY287D40F4WB"  My printers are working fine before I modify the conf but once I add to the URI I am no longer able to print.  Is there something I am missing?

---

