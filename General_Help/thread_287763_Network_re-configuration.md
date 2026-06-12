---
title: "Network re-configuration"
date: 2006-10-29
forum: General Help
---

### Post by DesignerX on 2006-10-29
It seems I messed up my network adapter configuration since it won't connect anywhere. (Giving "Network unreachable.." message)

How can I reconfigure it like it does when first installing ubuntu ?

thx

---

### Post by DesignerX on 2006-11-02
Come on, no one knows how to configure a network adapter ???
Its a basic thing (which unfortunatly I don't know) like doing sudo

---

### Post by Iowan on 2006-11-02
Its a basic thing (which unfortunatly I don't know either)...

I'm sure you've checked the usual spots - **/etc/network/interfaces**, **ifconfig**, **dmesg|grep eth**, System>Administration>Networking...
If it was set up for DHCP, will **sudo dhclient** retrieve an address?

Is this the configuration you're asking about - or are you asking about (re)loading drivers?

---

### Post by DesignerX on 2006-11-04
First, thanks for replyinh
Second,
I remember when installing ubuntu it reached a phase where it detected and configured the network adapter, thats what I'm looking for.

---

### Post by daimoh on 2006-11-04
I'd  be very interested in learning how to run that configuration too... if at all possible... anyone? Please?

---

### Post by dbott67 on 2006-11-04
According to [this site]("http://www.linuxforums.org/network/ask_dr._unx.html"), Debian-based distros run a hardware detection program called "discovery" at boot time (you can 'man discovery' to find out how to run it yourself).

The link above walks through how you can do everything manually by grepping dmesg, checking lspci to determine chipset, using lsmod to list loaded modules, modprobe to load, editing the /etc/network/interfaces and then stopping/starting the networking service.

-Dave

---

