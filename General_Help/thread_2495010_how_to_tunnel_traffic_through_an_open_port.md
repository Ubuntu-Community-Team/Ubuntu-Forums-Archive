---
title: "how to tunnel traffic through an open port"
date: 2024-02-04
forum: General Help
---

### Post by gregw2023 on 2024-02-04
I have two networks between which only one port 1433 is allowed. Both networks have Ubuntu servers, is it possible to redirect traffic (ports 80 and 443) to use port 1433 for the Apache server serving the http site ?

the architecture looks like this

------[ubuntu serwer 10.0.1.1] ---- [FW only 1433 allowed] -----[ubuntu serwer 10.10.1.1]-------


what should I use and what should the configuration look like?

---

### Post by TheFu on 2024-02-04
Use a VPN with correct routing between them.  I use wireguard.  There are many how-tos for this.

Or you could use a mesh-overlay network, like opennebula.  Some routers block the necessary traffic, but many don't.

The VPN aspect is required because you want multiple ports.
You could use an ssh-tunnel between them too by setting up an ssh-socks proxy, but ssh needs to be open to the other network for this to work and I think SOCKS is only for web-traffic.  I use this when traveling and I don't want a full VPN, but still want to access my home LAN web servers - like nextcloud and jellyfin and wallabag and calibre and about 20 others. This is for a single client, not an entire network.

You'll need some way to ensure that routing to the entire client-side of the network knows how to get to that gateway, down the tunnel and knows about the IPs/DNS on the other side.  This is why something like wireguard is probably the easiest. But you'll still need to ensure the client subnet knows all the IPs on the other side.

---

### Post by SeijiSensei on 2024-02-04
I use hoary old applications like xinetd and tcpproxy for things like this. The latter is now my preferred choice; I had to build it from [source]("https://fossies.org/linux/privat/old/tcpproxy-2.0.0-beta15.tar.gz/meta.html").

---

