---
title: "Setup Static (IPV4) LOCAL IP Addresses and now can't find computers on Network"
date: 2015-05-19
forum: General Help
---

### Post by 777funk on 2015-05-19
I did this to 3 computers on my home network:

> It's straightforward to set a static internal IP address on the PC. Open the properties of the network adapter (the route to that varies depending on which OS you use). Select TCP/IPv4, and click Properties. Now, before entering any data, go to the web interface on the router, and check the range of the DHCP server. Armed with this information, set the fixed IP address in the Properties of the TCP/IPv4 window to be something outside the range of the DHCP server. Set netmask to be 255.255.255.0 and the gateway to be the IP address of the router. Set the DNS server in the TPC/IPv4 window to be the IP address of the router.

That will set an static IP address on the PC, you can now adjust the router to forward the ports required to the new static IP address. The PC will remain behind the firewall and NAT, so it's quite safe enough.

 so I would have fixed IP addresses locally (vs auto assigned and changing every bootup). 

And I'm no longer able to see any of my machines on the network. Curious why this is and if there's an easy fix?

---

### Post by steeldriver on 2015-05-19
"see" as in what exactly? ping? network shares?

It's hard to say what happened without know how your router is set up and what numbers you entered specifically

Regardless, if the router supports DHCP reservations that would almost certainly be an easier and more maintainable solution

---

### Post by SeijiSensei on 2015-05-19
If you mean you cannot access the machines by their names rather than their IP addresses, that's because many routers operate as a DNS server and build the database of IP<-->hostname pairs as they allocate addresses.  If you use static addresses, you'll need to populate the DNS server manually, or use reservations as steeldriver suggests.

---

### Post by 777funk on 2015-05-20
> **steeldriver said:**
> "see" as in what exactly? ping? network shares?

It's hard to say what happened without know how your router is set up and what numbers you entered specifically

Regardless, if the router supports DHCP reservations that would almost certainly be an easier and more maintainable solution

I agree and that was my first preference but the router is pretty basic and doesn't give the DHCP reservation option. And I'm not *seeing* network shares btw. 

> **SeijiSensei said:**
> If you mean you cannot access the machines by their names rather than their IP addresses, that's because many routers operate as a DNS server and build the database of IP<-->hostname pairs as they allocate addresses.  If you use static addresses, you'll need to populate the DNS server manually, or use reservations as steeldriver suggests.

So it sounds like nothing will show up in Network Places (Windows) or Network (on Linux). I don't mind them showing as the IP and don't need names, is there a way to make that happen?

---

### Post by SeijiSensei on 2015-05-20
You can refer to the machines in Windows with \\ip.addr.of.server\share.  In Ubuntu it may depend on the distribution.  I use Kubuntu which allows you to enter a URL like smb://ip.addr.of.server/share into the file manager, Dolphin.  I think that works with some other file managers, but someone else will have to confirm that.

Another option is to add entries to the client's hosts file; you can do that in [both Windows and Linux]("http://en.wikipedia.org/wiki/Hosts_%28file%29"). Then you can use the hostname instead of the IP address.  That works well if you have just a few clients to manage. Large networks typically use a DNS server for this purpose.

---

### Post by 777funk on 2015-05-20
There they are! Thanks and wow! For the record, that works well in the Xubuntu's Thunar file manager as well. Is there a way to make them automatically show up in the file manager network tab (vs manually typing in the IP each boot)? Maybe the second option you listed?

---

### Post by SeijiSensei on 2015-05-20
I don't know about Thunar; in Dolphin I can just drag the folder icon and drop it in the left-hand navigation panel.  That works for connections that use SSHFS as well, with the fish://server/share/ URL in Dolphin.  That's how I move files between my local network and my cloud webserver.

---

