---
title: "Can't get ubuntu to reply to RARP packets"
date: 2015-02-01
forum: General Help
---

### Post by Tarran on 2015-02-01
Hi, I have a Sun Microsystems Ultra Enterprize 450, due to certain circumstances (outdated DVD drive firmware, no USB, damaged filesystem) I have no option but to netboot the system. This system is connected to 2 laptops, both running ubuntu (one for serial interface, one for netboot file server).

My problem is that the E450 machine can only netboot using RARP and tftp. And despite hours upon hours of work I can't seem to get the file server machine to reply to a single RARP packet from the E450. I'm using Netshark to check it's connection and it shows RARP packets being recieved by the file server, but no replies.
I'm using rarpd on the file server. Iv'e looked through every guide i can find, iv'e asked #ubuntu irc, i just can't get this to work.

Any advice would be greatly appreciated.

---

