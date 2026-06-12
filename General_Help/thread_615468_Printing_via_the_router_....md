---
title: "Printing via the router ..."
date: 2007-11-17
forum: General Help
---

### Post by asearle on 2007-11-17
I have a router with a USB port connected to a printer.

The printer has no network card.

Here I find that I can send jobs to the printer under Kubuntu by setting the print interface to ...

Printer type:  IPP Printer
URL:             [http://192.168.1.1:9100](http://192.168.1.1:9100)

... yippee!

However, the printer prints the following ...

POST / HTTP/1.1
Content-Length: 286
Content-type: application/ipp
Host: 192.168.1.1
User-Agent:  CUPS/1.3.2
Expect:  100-continue

... then comes a line of gobble-di-gook and nothing else.

I am using the same driver as with the same printer connected local (which works fine) and so am a bit bemused.

So my question is whether printing over ubs via a router is possible.  And whether the Network Printer w/IPP (IPP/HTTP) is the correct option to use?

Many thanks for any tips that you can give.

Regards,
Alan.

PS:  Now I tried deinstalling and re-installing all my printers and find that although I can connect locally, when I try to change the interface to 'IPP/HTTP', I get a message:  
Error - System Settings
Unable to change printer properties.  Error received from manager:
Requested operation cannot be completed.

I rebooted and tried 'Administrator Mode' but that didn't help.

Any ideas?

---

### Post by asearle on 2007-11-17
I've been trying various options under the print-option 'interface' and assume for connecting over the LAN via my router's usb port to the printer ...

Local printer > no, not this
Remote LPD queue > this would be printing via another Linux PC?
SMB shared printer > this would be printing via a windows PC?
Network printer (TCP) > if the printer has a network card (mine doesn't)
Remote CUPS server > it's not this, is it?
Network printer w/IPP > This seems to be the most likely but I can't get it to accept my entries

Other printer type > Or could it be here?

It would be great if someone could give me some tips or point me towards a good howto because this would be such a useful feature if I could get it to work.

Many thanks,
Alan Searle

---

### Post by asearle on 2007-11-17
I have been googling like mad to try to get this to work but all the messages seem to assume that the print server has some intelligence or the printer has a network card.  With mine neither of these is the case.

The router has a usb port connecting to the printer.

Under windows I found that all I needed was the driver software on my PC, nothing installed on the router and then the following settings under /printer/properties/ports ...

Standard TCP/IP port
Port Name:  my_port
IP Address: 192.168.1.1
Protocol:  raw  (not LPR)
Port number:  9100

... then it printed fine.

Under linux (Kubuntu 7.10) I have the driver installed and can get some output (as mentioned) but this is only random characters.

What I really need to know is how to duplicate these settings under Kubuntu ?

Or are there some other tricky things that I need to do?

Or maybe it isn't possible?

Or would it be better for me to buy a network card for the printer (but that's expensive).

Any tips would hopefully help me cure my frustration  :-)

Many thanks,
Alan.

---

### Post by asearle on 2007-11-18
Yipppeeee!

The settings that I needed in order to do this turned out to be ...

System Settings / Printers / myprinter / properties / interface ...

Network Printer (TCP)
Address: 192.168.1.1
Port: 9100

(i.e. the address is my router and the port is the same one as I was using under Windows)

I am soooo happy.

Cheers,
Alan.

PS: Is there a flag that I can set to declare this subject as 'solved'?

---

