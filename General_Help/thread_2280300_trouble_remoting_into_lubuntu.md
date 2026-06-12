---
title: "trouble remoting into lubuntu"
date: 2015-05-29
forum: General Help
---

### Post by tim119 on 2015-05-29
I have a fresh install of lubuntu 15.04 that I a need to be able to access and share the local users desktop for remote troubleshooting.  I have setup tightvncserver but it gives me a separate desktop environment and not the local users shared access.  I also tried xrdp and tried accessing via windows RDC but it gives me a blank grey screen.  Is there a way I can do this?

The project I am working on is to setup intel nuc fanless thinclients that will RDP to a windows remote desktop server but I need to still have remote access to the thinclient to help troubleshoot and see what the users are seeing.

Tim

---

### Post by TheFu on 2015-05-29
RDP and VNC are NOT secure. If used over a WAN/Internet, then a tunnel or VPN is mandatory.  You will not see exactly what the user sees either, but you will be able to reproduce the issue with the client's help.

I use x2go for remote desktop into Linux desktops. It feels 2-3x more efficient than VNC/RDP AND it uses ssh authentication (ssh-keys can be used) and tunneling. That is part of the protocol and only the ssh port needs to be opened. Best to run that on a non-standard port along with fail2ban - or something similar.  After all, 95% of admin work is done through ssh anyway.

None of these are "thin clients", but they will not tax a current NUC, provided you do NOT run 3D graphics desktops. Actually, no remote desktops work well (or not at all) with heavy desktops. Most people run LXDE or XFCE for this stuff - not Unity (I don't think it is supported).

---

