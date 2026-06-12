---
title: "Troubleshooting network issues"
date: 2008-01-04
forum: General Help
---

### Post by Sol1 on 2008-01-04
Hey guys,

I've finally made the complete conversion to Ubuntu by wiping Windows out of my last bastion of MS-infiltrated misery - my work laptop. I'm running Gutsy on a number of machines but this is the only one I'm having trouble with. 

Compaq nc8430
1.5GB RAM

The problem is with my network connection.  It drops unexpectedly every 5 or 6 minutes during the course of normal work (no heavy-lifting involved) and pops back up 15 or 20 seconds later.  I've monitored all of the logs (I expected to find something in the messages log) but there are no log entries that correspond with the hiccups.  

I had moblock and TOR installed but have since removed them thinking they may be contributing to the problem, but it's still happening.

Does anybody have any suggestions for further troubleshooting the problem?  I've searched high and low, but it's still annoying the hell out of both me and my IM buddies when I drop off every few mins.

Thanks!

---

### Post by icheyne on 2008-01-04
Are you sure it's Ubuntu? I was having similar problems with my ISP.

---

### Post by fragos on 2008-01-05
You didn't say wired or wireless.  I've seen this with wireless but it is specific to particular networks.

---

### Post by Sol1 on 2008-01-07
I don't think it's necessarily Ubuntu.  It very well may be hardware.

The problem is with the wired connection.  My wireless connection is working perfectly, it's just when I'm physically plugged in that I have problems.

---

### Post by fragos on 2008-01-07
If you don't use an RJ jack the wires that make the content can become oxidized which can prevent a good electrical connection.

---

### Post by ModelM on 2008-01-07
The Ethernet port on my laptop has small lights which indicate link & activity. If yours also has such lights, check them for a change when the connection drops. And the same for the lights on the hub/switch/router you are connected to, if it's accessible.

Nothing noted in the logs is significant. This would seem to indicate that the operating system doesn't "see" any change when this happens, perhaps pointing to a problem outside your laptop.

If you are connected via DHCP, is it possible for you to connect using static settings? This might show if it's a DHCP lease problem.

---

### Post by 5circles on 2008-01-12
Was the system working properly in Windows before you converted to Ubuntu?

I have an HP Pavilion Desktop running Windows Media Center that had an unreliable network connection.  I ended up installing a second NIC, and connecting them both to the router.  I'm not sure whether the problem was originally a poor physical connection (I did discover that as well at one point) because I moved and reconfigured everything.

Mike

---

