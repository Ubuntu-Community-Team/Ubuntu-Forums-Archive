---
title: "Who do I make my router work w/ Gutsy?"
date: 2008-01-10
forum: General Help
---

### Post by kris2pe on 2008-01-10
I have a linksys wrt54g & I want it to work w/ Gutsy. 
Any ideas?

---

### Post by KCPokes on 2008-01-10
It is a bit vague.  Work in what regards?  Wired or wireless?  The router will work, regardless of the OS; it is just a matter of making sure you have Gutsy set up correctly.  For wireless you'll need to ensure your wireless card is functional after the Gutsy install.  If it is functional, use Network Manager or WICD to find your SSID, at which time you set up your wireless connection as you would in Windows.

For wired, if you are using DHCP, it should just be a matter of connecting and the router will assign the necessary information.

---

### Post by freymann on 2008-01-10
> **kris2pe said:**
> I have a linksys wrt54g & I want it to work w/ Gutsy. 
Any ideas?

Ok, so plug the router into your internet source (DSL/Cable Modem) and then connect your Gutsy box to the router.

You can do a manual config of the router by pointing your web browser to

[http://192.168.1.1](http://192.168.1.1)

assuming you got an IP from the router OK. If not, you'll need to manually config your network interface with an IP, say 192.168.1.10, subnet mask 255.255.255.0 and gateway of 192.168.1.1. Your DNS can be 192.168.1.1 too.

Without anything more specific, your router should work.

---

### Post by kris2pe on 2008-01-10
> **freymann said:**
> Ok, so plug the router into your internet source (DSL/Cable Modem) and then connect your Gutsy box to the router.

You can do a manual config of the router by pointing your web browser to

[http://192.168.1.1](http://192.168.1.1)

assuming you got an IP from the router OK. If not, you'll need to manually config your network interface with an IP, say 192.168.1.10, subnet mask 255.255.255.0 and gateway of 192.168.1.1. Your DNS can be 192.168.1.1 too.

Without anything more specific, your router should work.
I already got the thing working on my xp. But It doesn't seemed to function on Ubuntu. 
but I have configured my Ubuntu to auto dial on my pppoe how do I change that?
I used the  pppoeconf to do that! 
How do I undo that?

---

### Post by freymann on 2008-01-10
> **kris2pe said:**
> I already got the thing working on my xp. But It doesn't seemed to function on Ubuntu. 
but I have configured my Ubuntu to auto dial on my pppoe how do I change that?
I used the  pppoeconf to do that! 
How do I undo that?

 Awh, that's even easier then.

 I have Ubuntu 7.10 Gutsy (you didn't mention what you have) so I can give you instructions for my version (it's the only version of ubuntu I've used).

 Click System>Administration>Network

 You should see the types of connections available. I'd click on the wired connections and then the properties button. Set it for automatic configuration DHCP.

 If the other connections talk about PPOE disable them.

---

