---
title: "Iptables redirect by mac"
date: 2016-01-27
forum: General Help
---

### Post by Glenn_Clark on 2016-01-27
Hi all

Still getting my head around iptables and could do with a little help on this 1.

We have a product which requires access to our server from an external addresses for configuration details. 1 or 2 of these items from time to time will need to access via a different server public ip address which can't be changed on the product. we know the mac address of these products in advance and I would like to redirect these products using the mac address.

I have been trying to find the answer online but not much luck and have come up with this so far which I can get working

iptables -t nat -A PREROUTING -m -–mac-source 00:04:13:aa:aa:aa -p tcp --dport 80 -j DNAT --to-destination 217.50.X.X:80

Any help here would be great

thanks

Glenn

---

### Post by Habitual on 2016-01-27
the port at the end of 
```
iptables -t nat -A PREROUTING -m -–mac-source 00:04:13:aa:aa:aa -p tcp --dport 80 -j DNAT --to-destination 217.50.X.X:[COLOR=#ff0000]80[/COLOR]
``` is surely 
incorrect, as you have a "dport 80" option already.

The rest? I don't know.

---

### Post by Doug S on 2016-01-27
If I understand the question correctly, the external servers are somewhere on internet, i.e. not on your local area network (LAN). If that is true then you can not implement iptables rules based on MAC addresses. Why not? Because the MAC address of the originating server is no longer present in the packet. The source MAC address in the packet will be that of the router / gateway. Source and destination MAC addresses only persist within a LAN.

---

### Post by Glenn_Clark on 2016-01-27
Would this still be the case for a hosted server as we have full public ip access.

---

### Post by Doug S on 2016-01-27
> **Glenn_Clark said:**
> Would this still be the case for a hosted server as we have full public ip access.Yes, I think so. For example, I have two public static ip adresses, but I still only get the MAC address of my ISP's gateway IP address for any traffic coming from outside of my public sub-net into my externally facing server.

---

