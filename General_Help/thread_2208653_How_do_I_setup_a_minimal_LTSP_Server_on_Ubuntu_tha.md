---
title: "How do I setup a minimal LTSP Server on Ubuntu that will rdesktop to a virtual machin"
date: 2014-03-01
forum: General Help
---

### Post by greavette on 2014-03-01
Hello,

I've been searching for an ltsp forum to assist but couldn't find one. If there is a better place to post this please let me know.

I'm looking for assistance on how to setup an ltsp server in a VM (KVM using Proxmox).  Each LTSP session would autostart an rdesktop session to a Windows virtual machine (KVM using Proxmox).  Basically the ltsp session would not be used as a desktop.

I'll be using berryterminal to connect a Raspberry Pi to the LTSP server.  When the LTSP Session was connected too from the Pi, the rdesktop script would started (maybe I'll use cron...or is there an autostart option that would allow me to do this).

I'm not using PXE Boot.  The LTSP session we connect to do not need Internet Access. Our office network already has a DHCP server.  

Please assist with how I would set up this minimal ltsp server with multiple sessions whereby each session can be connected to by a Raspberry Pi and auto start an rdesktop session to it's own windows virtual machine.

Thank you.

---

