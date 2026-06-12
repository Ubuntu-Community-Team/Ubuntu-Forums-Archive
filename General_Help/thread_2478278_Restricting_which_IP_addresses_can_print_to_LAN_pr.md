---
title: "Restricting which IP addresses can print to LAN printer"
date: 2022-08-21
forum: General Help
---

### Post by chellrose on 2022-08-21
I have a non-internet-connected LAN with a single printer and several PCs on the LAN.  I want to prevent specific LAN IPs from accessing the printer, while allowing access for specific others.  I've tried simply deleting the printer from "Printers" on the appropriate PCs, but Ubuntu keeps adding it back in automatically.  How can I restrict printer access by IP address?  I will accept either a whitelist or blacklist method; the number of IPs on this network is small enough that either one would work well.

All machines on the LAN are running Ubuntu 20.04 with Cinnamon 4.4.8.

Thanks.

---

### Post by TheFu on 2022-08-22
If you don't want printers added, disable avahi.
```
sudo systemctl stop avahi-daemon 
sudo systemctl disable avahi-daemon 
```
Bet that will work.

Try it for a week and see if there are any repercussions that you cannot live with. It will stop .local system name resolution on the LAN, which could be a big headache.
There may be specific avahi settings to just disable IPP (port 631/tcp) from being announced/honored.  

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1753509](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1753509) has some other workarounds that helped some people, but not everyone.

---

