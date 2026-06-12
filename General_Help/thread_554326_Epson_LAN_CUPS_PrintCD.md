---
title: "Epson LAN CUPS PrintCD"
date: 2007-09-18
forum: General Help
---

### Post by stvnaln on 2007-09-18
Hi, I'm using an Epson R220 on a network with the CUPS manager through a Netgear WGPS606 wireless print server and Linksys WRT54G hardware router. 

If anyone wants to know how I got that to work: after configuring the Netgear wireless, I opened [http://localhost:631/](http://localhost:631/), and installed the printer through the CUPS / administration /add printer setup page selecting LDP type with addy asLDP:// IP1.IP2.IP3.IP4/L1where L1 is the physical port on the wireless print server.

Ubuntu sees the printer and it works correctly for normal printing. I want to use the Epson PrintCD software with WINE but get the following error when I try to make it print "The EPSON printer driver dealing with the cd is not installed". 
I was unable to install the driver using WINE, because for some reason the install manager wants to see the printer on a USB or virtual port and can't find it. 
I am open to using other software that can utilize the cd tray printing option on my printer.
Any suggestions?

---

### Post by stvnaln on 2007-10-14
I have found a solution for this problem.
 If anyone else is using an Epson R220 or similar Epson printer that uses the PrintCD Epson software to print directly on a printable surface CD, GIMP is one substitue (better IMHO) that can be used by following the instructions I found here:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R200](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_R200)

---

