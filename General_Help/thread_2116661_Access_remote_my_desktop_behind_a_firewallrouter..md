---
title: "Access remote my desktop behind a firewall/router."
date: 2013-02-16
forum: General Help
---

### Post by Trip4004 on 2013-02-16
I would like to make a remote connection with my ubuntu 12.04 LTS desktop.
That is behind a router/firewall. I have no access to the firewall and the router, so port forwarding is not an option.
Teamviewer should do the trick but I'm not around to get the id and pass. And all other options I have found do not support Linux.

When I'm in the same LAN there's no problem.

---

### Post by steeldriver on 2013-02-16
is ssh already forwarded? if so you should be able to set up an ssh tunnel for the VNC (or RDP) traffic

---

### Post by Trip4004 on 2013-02-16
I can't add anything in the IP-tables. Even if it was open how should it be forwarded to my host among 100 others?
There has to come in a third party I suppose.

---

### Post by gordintoronto on 2013-02-16
> **Trip4004 said:**
> .... I have no access to the firewall and the router, so port forwarding is not an option.


In that case, you can't do what you want to do.

---

### Post by SeijiSensei on 2013-02-17
If you only need to connect from one or a few locations with known fixed IP addresses, you could configure the machine behind the firewall as an OpenVPN client (with OpenVPN's "remote" directive) and set up a tunnel with the viewing computer.  I manage some servers this way.  Even though I have no control over the firewall or local networking infrastructure, the server connects to one of my virtual machines with a static IP and sets up a tunnel.  I use [static-key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") tunnels in these cases as they are easy to set up.

Once the tunnel is established, you can run "ssh -X" to the remote's tunnel address and use either text-mode or graphical applications on the remote.

---

