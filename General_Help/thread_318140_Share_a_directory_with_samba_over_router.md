---
title: "Share a directory with samba over router?"
date: 2006-12-13
forum: General Help
---

### Post by johann_p on 2006-12-13
I would like to share a certain directory from my PC with other PCs. However, those PCs are not on the same (wired) LAN. Instead, they are part of another LAN that is connected to my LAN via a router.

Here is the setup: 
  My LAN is connected to a router that is connected to the internet and does NAT. My computer is connected to that router as well as a WLAN router.

So the WLAN router gets its IP from the WAN router and the WLAN router has its own LAN to which several computers are connected.

What I want is to share my directory so that the PCs on the WLAN can use it. And maybe also, access shares that are made available by these PCs.

Both the WAN and the WLAN routers do NAT and can forward ports, but they cannot forward a port to a different port on the target machine.

Any chances to make this work?

---

### Post by johann_p on 2006-12-13
OK, this seems to work, at least in the direction from my PC to the PCs on the WLAN, which is what I mainly want. 

I have not yet figured out how I can let different users have different access rights to the directory I share ... 

The share is configured as "writable = yes" in the config file, but I still would like some users to only have read access.

---

