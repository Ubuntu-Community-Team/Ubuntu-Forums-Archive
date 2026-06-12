---
title: "XDMCP and LUbuntu 20.04.1"
date: 2020-10-18
forum: General Help
---

### Post by David_Partridge on 2020-10-18
I realise that the display manager has changed to sddm.  I was however a bit surprised to find that sddm doesn't do XDMCP.

So how do I get GUI login and access using XDMCP to my LUbuntu 20.04.1 system?   Should I install l LightDM and re-configure the system? How?

Or is there some other solution that gives me the remote graphical access that I need?  I don't mean by the way SSH and running an XTerm, I mean a fully fledged desktop login.

I understand that the sddm developers decided not to support XDMCP on the grounds it was insecure.

I'd argue that it should be my decision whether or not to use XDMCP on my local LAN.

Thanks
David

---

### Post by TheFu on 2020-10-18
**x2go** over the internet w/ssh; all nx protocol uses ssh
or
**xspice** on the LAN. Spice works easiest into virtual machines running under libvirt and kvm. I've not gotten it working directly on hardware installs.  Spice is speedy fast, local or on the LAN.

I've been using x2go daily for years. Out of the remote desktop solutions, it is both secure and fast.

---

