---
title: "Please Help before I reinstall! Printing disappeared."
date: 2006-11-06
forum: General Help
---

### Post by Boelcke on 2006-11-06
Sigh. I just wanted to sit down and work, and not mess with improving my ubuntu installations, and something just stopped working.

I have two ubuntu PCs, a main PC that I share with my wife, still running hoary, and a second PC, running dapper.  I have a Brother HL-2040 attached to the hoary PC.  When I finally got the right driver installed, the CUPS printer just appeared on the dapper PC, and everything worked well.

Today, there's no printer on my dapper PC.  When I try to print with an application, the app hangs.  When I select System, Administration, Printers, it sits for a while with the busy mouse symbol, and no window ever appears.

This all started earlier, and I just got a random error message saying that the CUPS server could not be contacted.

I'm looking for any suggestions on how to go about fixing this.  Can I re-install the "printers" part of ubuntu?  How?

---

### Post by Boelcke on 2006-11-08
Er, nevermind.  It turns out that I hooked the TiVo up to the network, which took the first IP address from the router's DHCP.  I had 

ServerName: 192.168.1.100

set in the /etc/cups/client.conf file.  When the main PC (that the printer is hooked up to) bumped up to 101, this PC couldn't find the CUPS server, and just hung.

Now if I can just figure out how to get the name to stick to the box, and I'll stop referring to it by an IP address...

---

