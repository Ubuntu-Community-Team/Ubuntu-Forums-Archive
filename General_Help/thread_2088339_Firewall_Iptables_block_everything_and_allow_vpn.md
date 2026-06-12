---
title: "Firewall Iptables block everything and allow vpn"
date: 2012-11-26
forum: General Help
---

### Post by msm25 on 2012-11-26
Hello,
 
I am confused about how vpn works in a freeradius enviromment. When we connect to a VPN on a Windows 7 to a VPN server, what is the default gateway? Will it use the port 80 of the vpn server or will it use the default gateway of his own computer? If he uses his default gateway, how can we block access to a specific service? will the iptables on the server be able to block his traffic?
 
I would like to block all traffic on my ubuntu server with iptables and them allow only the protocols : HTTP, HTTPS, PPTP, L2TP, SSTP,OpenVPN and the comunication between this server and a FreeRadius server
 
My understanding might be wrong, any help will be appreciated
 
Thank you

---

### Post by The Cog on 2012-11-26
I am assuming that win7 is your VPN client and that ubuntu is your vpn server. Not that it matters that much.

A vpn connection really just provides a network connection between client and server, like a new LAN connection directly between them. There is no reason here why the client would not continue to use its normal default gateway, ignoring the VPN.

So many VPNs go further, and deliberately override the default gateway in the client, so that the default route is now across the VPN. This is an option in OpenVPN (configured in the server), I don't know about any other VPNs. 

Of course, in order for the connection to the vpn server to still work when the default gateway is changed, the client must have an explicit route to the VPN server that does not use the tunnel, otherwise you have the vpn trying to use itself, whcih breaks things. This is extra route is added automatically by the client as it changes the default route.

If the client has had its default gateway changed, then you can configure iptables on the vpn server to filter the clients connections. You may want have different rules for traffic forwarded to/from the vpn interface (FORWARD chain) than you do for local connections from the server itself (INPUT and OUTPUT chains).

If the client does not have its default gateway changed, then there is nothing the vpn server can do to prevent the client from continuing to use the internet normally.

---

### Post by msm25 on 2012-12-01
Thank you for your explanation, very helpfull. 
 
I guess you don't know how to force a default gateway to be assign and the route to be added in a freeradius system with pptp and l2tp?

---

