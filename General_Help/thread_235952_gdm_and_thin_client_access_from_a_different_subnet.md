---
title: "gdm and thin client access from a different subnet"
date: 2006-08-14
forum: General Help
---

### Post by innovative22 on 2006-08-14
Hi everyone,

This is a bit of an odd one, and I am hoping someone can help me with it.

I have my main computer (Ubuntu) running as a gdm server, and when I plug into the local switch I am able to login remotely via a thin client on my laptop by using:

X -query MyIP (MyIP is the workstations local IP address)

I have a modded Linksys WRT54G acting as a wireless client and DHCP server in the basement (it was easier than running RJ45 cable).  Clients are assigned an IP on a different subnet, and although I can access all other open services on the main unit I am unable to login via gdm.  I get the grey checkered wallpaper and plain 'X' mouse pointer and then it hangs.  The wireless client has no firewall enabled and nmap shows that the xdm port 177 is listening.

Does anyone have any ideas?

Thanks and regards,

Innovative22

---

