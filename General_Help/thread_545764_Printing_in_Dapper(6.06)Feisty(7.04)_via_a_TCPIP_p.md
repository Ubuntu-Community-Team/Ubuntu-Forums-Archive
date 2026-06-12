---
title: "Printing in Dapper(6.06)/Feisty(7.04) via a TCP/IP print server without IPP support"
date: 2007-09-08
forum: General Help
---

### Post by ssmohan on 2007-09-08
Greetings,
   
    We need help printing in Dapper/Feisty to a PSC1210 (All-in-one) printer via an Airlink APSMFP210 multi-function print server that supports TCP/IP but not IPP.

   We are able to use all features of the PSC1210 from the Windows XP partition of the laptop.  when the PSC1210 is connected to the network via the Airlink APSMFP210 server.  We have also been able to use the PSC1210 for printing in linux when it was connected locally (via USB) to the laptop.  However, we cannot figure out how to print to the PSC1210 via the APSMFP210 server in neither Dapper(6.06 LTS) nor Feisty (7.04).

   We can ping the server at 10.0.1.254 successfully (our local network is 10.0.1.xx) and we have printed to the same printer via the same server on this network using the same laptop on Windows XP.

   We contacted the Airlink support staff and were told that:
> The APSMFP210 multifunction print server supports TCP/IP protocol. But it does not support IPP protocol.  If the Linux distribution only uses IPP protocol, then unfortunately you can not connect to it. But if it uses TCP/IP for printing purposes, then you may use the Network Wizard to detect the printer and set it as default.

  We cannot detect the printer in Dapper/Feisty when we access the printer set-up gui in system->administration->printing.   However, we noted the TCP/IP settings used in Windows XP and found that we can ping  the same IP address (10.0.1.254)  in both Dapper/Feisty.  However, no printer is detected in linux.

  Is there a how-to on configuring a print server which supports TCP/IP but not IPP ?

Thank you for your help.

---

### Post by K.Mandla on 2007-09-08
Moved to General Help. ;)

---

### Post by ssmohan on 2007-09-08
Greetings,
    I have included some additional data from the Windows XP partition.  When the PSC1210 is connected to the network via the Airlink multi-function print server, the properties of the printer are listed as:

> PORT USB001  Virtual printer port for USB hp psc 1200 series
Print Processor  WinPrint RAW
bidirectional support enabled

Does this mean that I should be able to print in linux with the raw setting ?  How do I define a USB virtual port in linux ?  The connection from the laptop to the print server is ethernet (10.0.1.254 is the address of the print server) and then the connection from the print server to the printer is via usb.

Thank you for your help

---

