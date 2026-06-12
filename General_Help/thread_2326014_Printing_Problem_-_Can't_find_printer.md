---
title: "Printing Problem - Can't find printer"
date: 2016-05-27
forum: General Help
---

### Post by stephen67 on 2016-05-27
I am using Ubuntu 14.04
Printer is Epson WF-2630
Wi-fi connection. Hard coded IP address

When I try to print, I get a Gnome pop-up saying printer is off-line. Using the web interface to CUPS the reported error is printer not found.

I can always ping the printer.
I can always print from a windows computer on the same network.

I can, from the CUPS web interface "modify" the printer settings. I click through without changing anything.

When I am finished, the stalled print job is printed.

Any ideas how I can print without "modifying" the printer settings?

Stephen

---

### Post by gsahli on 2016-05-27
What print comm protocol are you using?
Please be clearer about IP addresses - are you trying to print directly to the printer (called ad hoc mode) or does the printer have an IP address that's reserved in your router?

---

### Post by stephen67 on 2016-05-29
The printer's MAC address is set to a permanent IP address in the router's DHCP table.

In the CUPS configuration I specified the printer's IP address.

Since I am using CUPS, I assume I am using IPP.

The windows computers print directly to the printer as well.

---

### Post by gsahli on 2016-05-29
I wouldn't assume IPP. Either try mDNS/Avahi or HP socket-jetdrect. or even smb:\\<IP address>

---

### Post by him610 on 2016-05-29
Sounds like you have a configuration issue which may cause your problem. You may need to experiment with protocols a bit.
FWIW, I have two network printers from different manufacturers. For each printer, in the printer properties field, Device URI: both have "socket://192.168.1.xx"
The IP address for each has been set in each printers setup routine. Just reserving the IP address in your router is not good enough. It must be set in the printer.

---

### Post by gsahli on 2016-05-30
If you have a network printer without front panel, that uses DHCP to get an IP address, the address reservation in the router is the way to insure the printer is always found at a specific IP address.

---

### Post by efflandt on 2016-06-01
him610 are you sure that you see everything in the Device URI field? Ignoring the IP part mine are "socket://172.16.0.69:9100", the :9100 is the first JetDirect port which most printer servers can do along with lpr/lpd printing, IPP (cups), Windows and Apple zeroconfig. For some reason my system duplicates the printers that I configured, so I gave them descriptions to tell which I configured. I don't use samba for anything, so maybe avahi-daemon (which does Apple zeroconfig) is automatically adding the duplicates.```
efflandt@XPS-8100-1404:~$ avahi-browse -lta
+  wlan0 IPv4 Lexmark X204n-zero    Internet Printer     local
+  wlan0 IPv4 Lexmark C543dn-zero   Internet Printer     local
```

---

