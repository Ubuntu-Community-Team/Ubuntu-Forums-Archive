---
title: "OpenVPN, internet access for clients"
date: 2019-10-02
forum: General Help
---

### Post by ozkan on 2019-10-02
Hi

I have an Open VPN server, my clients can connect to my server and can ssh to my server no problem on that. But the problem the moment they connect to server they are loosing all their internet connections. 
can you please guide me for the points that I need to check.

thanks in advance

---

### Post by TheFu on 2019-10-02
Seems you want a "split vpn tunnel".   With that terminology, perhaps you'll be able to find a solution?  It should be in the routing.  Google found this: [https://forums.openvpn.net/viewtopic.php?t=8229](https://forums.openvpn.net/viewtopic.php?t=8229)  Don't know if it will work or not.

---

### Post by SeijiSensei on 2019-10-03
Are you trying to route all the clients' traffic through the tunnel? That's always complicated. Can you run the command "route -n" on a client machine both before and after connecting to the OpenVPN server and post the results?

---

### Post by ozkan on 2019-10-05
I found out that I have fortgetten this 

> iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE

---

