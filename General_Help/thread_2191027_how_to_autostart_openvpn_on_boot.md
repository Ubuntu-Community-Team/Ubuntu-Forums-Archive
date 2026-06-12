---
title: "how to autostart openvpn on boot?"
date: 2013-11-30
forum: General Help
---

### Post by jj4 on 2013-11-30
I currently start openvpn using
sudo openvpn --client /etc/openvpn/myclient.ovpn

How can I make this happen at boot? If it needs sudo to run normally then can I use it during boot?
Do I just add this line into /etc/rc.local?

---

### Post by The Cog on 2013-11-30
Drop the configuration file in the /etc/openvpn folder. Perhaps put the certificates there as well, or in a subdirectory. Then which VPNs are autostarted is controlled by /etc/default/openvpn (default is to autostart **all** configuration files in /etc/openvpn). You may have to rename the config file extension from .ovpn to .config.

---

### Post by jj4 on 2013-12-01
> **The Cog said:**
> Drop the configuration file in the /etc/openvpn folder. Perhaps put the certificates there as well, or in a subdirectory. Then which VPNs are autostarted is controlled by /etc/default/openvpn (default is to autostart **all** configuration files in /etc/openvpn). You may have to rename the config file extension from .ovpn to .config.

but isn;t this autostarting the openvpn server?
I want to autostart the client connection

---

### Post by The Cog on 2013-12-01
The only difference is in the configuration file. A server that accepts connections from multiple clients will probably have the word "server" in the config file. A client is more likely to contain a line like "remote 1.2.3.4" instead.
Whether it autostarts or not is independent of that.

---

