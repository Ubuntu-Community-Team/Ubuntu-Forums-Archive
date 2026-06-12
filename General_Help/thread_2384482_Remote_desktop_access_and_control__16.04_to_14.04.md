---
title: "Remote desktop access and control  16.04 to 14.04"
date: 2018-02-07
forum: General Help
---

### Post by Robbyx on 2018-02-07
My friend is unable to use Teamviewer and so I thought I would try to access her computer (across the internet) using remote desktop viewer (RDV) my end and  and the screen sharing option in Ubuntu settings on her machine.

RDV requires a host address

Do I ask her to supply me with her IP address from something like "whatismyipaddress.com" 

Do I have to add a port address and if so how do I  find which one?

Will this involve port forwarding on her machine, because she does not have access to the router. If so Is there a way of avoiding port forwarding?

---

### Post by TheFu on 2018-02-07
Not using port forwarding makes this much harder.  You could setup a VPN server between her and you, then using that tunnel.  YOU will need to do port forwarding on your side.

Really, using ssh would be much easier than any remote desktop.

---

