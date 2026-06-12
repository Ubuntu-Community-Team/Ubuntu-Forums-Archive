---
title: "Trouble with a static IP address"
date: 2007-03-14
forum: General Help
---

### Post by grte on 2007-03-14
So, I'm behind a router and trying to set up a static IP address.  I can do this successfully, just a simple matter of setting the address and adding my ISPs DNS addresses.

However, upon reboot, the dns addresses have been removed from network-admin, so I can only connect to anything via IP address.

Does anyone know why this might happan and how I can fix it?

---

### Post by Kateikyoushi on 2007-03-14
Step 1) gksudo gedit /etc/resolv.conf add the IP to your ISP if you know them or to OpenDNS (208.67.222.222 and 208.67.220.220). Like "nameserver 208.67.222.222" add one line per server, a maximum of 3 servers. There should already be one IP there, use it as a pattern. Without step 2 this is useless. 

Step 2) gksudo gedit /etc/dhcp3/dhclient.conf 

add a line "prepend domain-name-servers 208.67.222.222,208.67.220.220;" (no quotes) The DNS servers here must be the same as in /etc/resolv.conf. The prepend stops the servers being ditched in etc/resolv.conf

Hope it helps.

---

### Post by grte on 2007-03-14
That doesn't seem to have any effect, I'm afraid.

This one is really confusing me, since this isn't an issue at all on the other PC in the house, which also runs Edgy.

---

