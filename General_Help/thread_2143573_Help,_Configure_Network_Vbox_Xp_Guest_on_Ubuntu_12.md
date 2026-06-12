---
title: "Help, Configure Network Vbox Xp Guest on Ubuntu 12.04 Host"
date: 2013-05-09
forum: General Help
---

### Post by sluxuer on 2013-05-09
Hello all,
I have a problem with setting up connection win xp guest between ubuntu 12.04 host, For Your Information :
I have Laptop asus a43sd with ubuntu OS, and I installed vbox on ubuntu.
I try to run Win xp on vbox as guest os, and run success.
I Try to connection xp between ubuntu, and succsess with conf:
Win XP :
Ip dhcp, connected to ubuntu, can access shared from ubuntu
Ubuntu :
Connect to internet with usb to phone modem, but i try to ping ip guest and not connected.
in vbox i set network on NAT, But after I disconected usb modem, guset os can't access shared folder from ubuntu, but the icon is connected.
I Try to change Bridge Adaptor, and i set to eth0 ubuntu 192.168.1.2, xp 192.168.1.3. in xp icon lan is connected but ping is RTO, in ubuntu still not connected.
Can you help me please??


Regrads



Jimmy

*sorry, for my words were less pleasing.:-)

---

### Post by dino99 on 2013-05-09
be sure to also have installed the vbox guest additions (watch Oracle virtualbox install howto url)

---

### Post by sluxuer on 2013-05-09
> **dino99 said:**
> be sure to also have installed the vbox guest additions (watch Oracle virtualbox install howto url)
This forum is amazing, it did not take long to get a response:p
if you mean like this? [http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

I have installed guest additions, but still cant solved. now :
my xp (guest)
icon lan still conected, but can't ping to ip host, can't access shared host.
my ubuntu (host)
description on network manager wired network disconnected, can't ping to ip guest.
I just want to connected, and i will learn about networking on ubuntu,,:(

Thanks for yor response

---

### Post by sluxuer on 2013-05-09
can anyone help me?:(

---

