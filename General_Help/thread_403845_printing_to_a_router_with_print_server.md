---
title: "printing to a router with print server"
date: 2007-04-07
forum: General Help
---

### Post by orlox on 2007-04-07
Hi. I have a d-link router with print server enabled and I'm trying to configure my ubuntu box to remotely print to it. In the network I have a windows box with this working using the following configuration:

port name: IP_192.168.0.1
Ip direction: 192.168.0.1
protocol: lpr
port number: 515
spool: lp1

How can I configure a similar thing on ubuntu????

---

### Post by solar george on 2007-04-07
You can use the gnome printer manager, when you add a new printer just select a network printer and "Unix (LPD)" and enter the servers ip address and the spool name when asked.

---

### Post by orlox on 2007-04-07
I tried that but it doesn't seem to work. I enter the spool "lp1" when it asks for it, but when I reopen the printer properties, the spool entry is empty :(

---

### Post by orlox on 2007-04-07
A while ago I find this

> 
5.5.4. Network Printers

Network printers are printers that have a built-in print server interface (such as the JetDirect interface in some HP printers) or printers connected to a print server box or a router box enabled as a print server. Windows machines offering printer shares are not print servers in the strict sense (although CUPS can handle them easily in a way similar to print servers).

In most cases, a network printer supports the LPD protocol, which uses port 515 for communication. Check lpd availability with the command:

netcat -z <hostname>.<domain> 515 && echo ok || echo failed
  

If such a server is available, CUPS can be configured to access it under a device URI, an address in the form lpd://server/queue. Read about the concept of device URIs in file:/usr/share/doc/packages/cups/sam.html. 


So I tried netcat and resulted in:

> 
root@PCPABLO:/var/spool/lpd# netcat -z 192.168.0.1 515 && echo ok || echo failed
ok


So I guess that I could set up the printer in cups....yet I haven't been able to find how to manually include a printer to do that :(

---

### Post by solar george on 2007-04-07
Try connecting thorough the web based CUPS config on 
[http://localhost:631/](http://localhost:631/)

---

### Post by orlox on 2007-04-07
Didn't knew cups had a web interface....yet, what user am I supossed to give when it prompts for username and password?? I tried with root but it wasn't accepted...

---

### Post by solar george on 2007-04-07
Try your user name and passwd.

---

### Post by orlox on 2007-04-07
Already tried...doesn't work either :(

---

