---
title: "can bash scan for IP addresses of wireless devices?"
date: 2008-02-17
forum: General Help
---

### Post by ibuclaw on 2008-02-17
Hi, does anyone know how to scan for wireless devices IP addresses?

I'm trying to connect to a printer, and all the threads I've read say I need the printer IP address to connect. And all I can acquire is a Hex? style address from the command: 
```
       :~$iwlist scan
          Cell 02 - Address: 82:A6:12:C9:99:1A
                    ESSID:"Olivetti ANY_WAY"
                    Mode:Ad-Hoc
                    Frequency:2.412 GHz (Channel 1)
                    Quality=7/70  Signal level=-88 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

```

Any help would be appreciated.

Thanks

Iain

---

### Post by KingWilliam on 2008-02-17
I don't know if I'm right, but I once had the same problem. I had to configure a Network Printer using the web interface, but nobody in the company knew the IP-address. This was a wired network. 

To find a device on the network it has to be in the same subnet, so to find the IP same problem. I found a tool in the menu from the printer itself (I've been pushing those damn small buttons and tried to read from the small screen indeed) with which I could print the device status. The IP address was included on the page that came out.

Maybe this could be helpfull to you...

Grtz, 

KW

---

