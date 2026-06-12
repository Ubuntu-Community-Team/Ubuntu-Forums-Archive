---
title: "Need expose a locally attached printer to my Ubuntu system's IP address, port 9100"
date: 2020-11-05
forum: General Help
---

### Post by wb0gaz on 2020-11-05
I have a Ubuntu 18.04 system with an inkjet printer locally attached via USB. Both are working (computer and printer.)

I now would like to make the printer available to other machines on my LAN, as a listener on port 9100 (AppSocket, JetDirect, etc.) so that other machines can make use if the printer at (IP address of my Ubuntu system) port 9100. 

I do NOT want to use SAMBA or Windows file/printer sharing, because I have a specialized (non-PC) device to use that can ONLY print it's output to an IP address with this mechanism.

The printer is PCL type (Deskjet) and the specialized device generates PCL (it opens a TCP socket, sends the PCL stream, and closes the socket). I've verified the device can talk to two other (different) PCL printers that are on the network (other IP addresses), however, that is not a workable solution; I need the Ubuntu-attached USB printer to provide this service.

After fiddling with netcat (-l -p 9100 > file) and lp (lp file) commands (to listen for a file on port 9100, then print it to the default printer using lp) and seeing the file show up in CUPS (localhost:631/jobs/) but not printing (hangs at "processing page 1" forever), I realize this is probably a case of "re-inventing the wheel" and I'd like to see if there's a normal way of going about meeting this requirement.

Thanks for any pointers/advice or recommendations as to where I could seek help for a task like this.

---

### Post by TheFu on 2020-11-05
Use IPP as the protocol on the "server", [https://ubuntu.com/server/docs/service-cups](https://ubuntu.com/server/docs/service-cups)

Ensure the firewall allows that port and CUPS is listening on the "server".

For linux clients, the printer setup dialogs should just work and prompt to install drivers, which you would select from the list. If none are showing up in the list, enter the IP address of the "server" or you can check that avahi is running.

---

### Post by wb0gaz on 2020-11-05
Thanks for the reply -

I'm pretty sure I need to use the "socket" protocol (port 9100), not IPP protocol (port 631). The instrument knows nothing of IPP, just knows how to open a TCP socket, write out some PCL data, and close the socket.

I've been searching for a step-by-step or example for CUPS setup in "socket" mode. I've *never* set up CUPS before, so I'm having some trouble finding a starting point, given my LAN IP address and the name of the locally (USB) attached printer. I believe I have port 9100 open on firewall as my attempt with netcat (netcat -l -p 9100 >tempfile) worked fine (the device deposited it's print output in tempfile, but I can't work out how to get tempfile to the printer!)

Thanks again,

Dave

Thanks!

---

### Post by HermanAB on 2020-11-06
CUPS make any printer look like an Apple Laser Writer II on IPP protocol.  It doesn’t matter what the printer really is - it can be a $10 ink jet. It will still work like a Laser Writer. As mentioned already, open your firewall (if any) with (iptables -F). Select a Laser Writer II on the machine that you want to print from and Bob’s Your Uncle. You don’t need Samba.  You don’t need to install a device driver.  All systems have an Apple Laser Writer driver by default - even Windows ME. Only if you want to do special paper jamming features like duplex printing, you may need a different device driver.

---

