---
title: "Help with Remote Desktop"
date: 2004-12-06
forum: General Help
---

### Post by killerfish on 2004-12-06
Hopefully, I'm just doing someting stupid and it's an easy fix.  I'm trying to use the Remote Desktop tool to connect to my Windows machine that's on the same router.. I can ping the host machine, but any connection I try (RDP, RDPv5, VNC) etc.  times out.  Here's what I've done so far:

1)  Setup router to forward port 3389 to appropriate IP address as indicated using ipconfig on windows machine and ifconfig in ubuntu.
2)  Enable Remote Desktop connection and opened Windows firewall for Remote Desktop on Windows Machine
3)  Installed Real VNC Server on windows machine to try that ...same result.

My setup is as follows:
Cable Internet -> Router -> Ubuntu & Windows machines plugged into router.

Incidentally, my Ubuntu machine is also a dual boot windows machine and I get the same problem when trying to do a windows to windows connection.  Net, I think it has to do with router/ports, but not sure.

Help! :)

Thanks
Killerfish

---

### Post by mr_ed on 2004-12-06
I believe setting IP forwarding on the router means that outside connections will get forwarded to your internal machines on those specified ports.  I'm thinking it has more to do with your Windows firewall settings, but that's just a guess.
One thing you could try is running a VNC server on your Ubuntu machine and try to connect the other way, for starters.  At least you would know that it's possible with your setup to make VNC connections.  :)  And make sure that your /etc/hosts.deny and /etc/hosts.allow files will allow VNC connections (that's probably a non-issue).

---

