---
title: "Two instances of Open VPN on the same box"
date: 2012-10-20
forum: General Help
---

### Post by nonentity133742 on 2012-10-20
I have Ubuntu Server 12.04 running on my box. I've been trying to get Open VPN working and understand keys, most of the config stuff, etc. What I'm having trouble with (and yes, I have tried google :P) is:   1. I need to get two servers out of the same /etc/init.d script at starup that run on seperate ports. This is probably a simple task, but I'm new to init scripts in general.   2. I need to get the first instance connected to my LAN only (all connections to 192.168.1.x/24 forward to me) and have all WAN connections go through the clients ISP.   3. The second instance has to push all data through the tunnel, regardless of it being LAN or WAN.   4. I don't really understand the difference between a TAP or TUN interface, so if someone could clear that up it would be great :D . I believe TAP gives the client a local IP form the LAN's DCHP capable router (which qould be great!)   So, I've been at this for about a week, if anyone knows how to do any of these, please post!

---

### Post by nonentity133742 on 2012-10-27
Ok, either I'm posting in the wron place, or nobody here knows about OpenVPN...

---

