---
title: "Adjusting VNC server preferences to allow trusted and untrusted clients?"
date: 2008-04-22
forum: General Help
---

### Post by dubref on 2008-04-22
I am trying to configure VNC server on my Ubuntu computer to allow both trusted clients (no password required) and untrusted clients (password would be asked for).

All machines are on a local network.  


Ubuntu 7.10 VNC server machine is 192.168.0.10
Windows XP "trusty" is 192.168.0.20
Windows Xp "untrusted" are 192.168.0.30 and 31

Using Remote Desktop Preferences i can toggle password requirement for all or none, but no advanced settings are possible. 

I would like to manually set which IPs (for example 192.168.0.20) would be deemed to be trusty and would not need a password and rest would be deemed untrustworthy and password (just one for all) would be required.

How would one go about setting up something like that?

  I have not made any adjustments to Ubuntu VNC server, except toggle preferences in Remote Desktop Preferences.

I imagine there must be some file which can be edited with these additional IP requirements. Or would I need to install different VNC server software?

Any pointers towards a solution would be very much appreciated. :)

PS Windows clients are using RealVLC viewer(works fine).

---

