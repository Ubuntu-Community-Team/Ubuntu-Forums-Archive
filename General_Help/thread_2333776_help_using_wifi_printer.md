---
title: "help using wifi printer"
date: 2016-08-12
forum: General Help
---

### Post by jrh74 on 2016-08-12
I get the following message when I try to print on my wireless printer From Ubuntu 16.04 LTS (Brother MFC-J4510DW).
 
 
          “Could not start printer.
            Please check your printer configuration.”
 
 
 I have no such problem when printing from windows 10 operating system.  Ditto with respect to printing from windows 10 on my laptop.   Is this something I have to take care of on my printer or is it about incorrect installation of printer in Ubuntu or maybe some fault with the way my network is set up?  Any help on how to get past this would be appreciated.
 
 
 Thanks,  
 John
 
 
 
 
 My system
 Mother board: ASRock Z77 Pro 4 with integrated sound and video  
 Hard Drive 1: WDOEM  WD1TB BLUE SATA6.0 HD (1000 Gb) w/Ubuntu 16.04 LTS Desktop OS
 Hard Drive 2: Toshiba (500 GB) w/Windows 10 OS
 Memory: CRUCIAL 8GB 4X2D3 1333 DIMM CL
 TV tuner: Hauppauge WinTV-HVR-2250 (two tuners)

---

### Post by SeijiSensei on 2016-08-12
Go to Brother's web site and download the "Driver Install Tool" for your model.  That will install the correct drivers.  You should then be able to point a browser at [http://localhost:631/](http://localhost:631/) and use the Admin tools to add the printer.  Usually CUPS will detect it automatically as it did with my HL-3170CDW.

I don't use the wifi feature of my printer, though.  I have it hardwired to my network router with an Ethernet cable and a static IP address.  Every one of my devices can see it, including my Android phone with the Brother app installed.

---

### Post by ajgreeny on 2016-08-13
You should also give the printer a static IP address.

This is probably most easily achieved from the router configuration page in your browser, choosing "Reserved IP addresses" or some similar section.

---

